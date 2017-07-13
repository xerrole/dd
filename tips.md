# Iframe loading timeout

    function setIframeSrc() {
    var s = "http://lx5.in/CGIT-Results-p2-2013.php";
    var iframe1 = document.getElementById('iframe1');
    iframe1.src = s;
    setTimeout(function(){
        if (window.stop) {
            window.stop();
        } else {
            document.execCommand('Stop'); // MSIE
        }
    }, 5000);
    }
    setTimeout(setIframeSrc, 5000);

# Output chinese to windows console

    | iconv -f utf-8

# Run multi django instance with single source package

Suppose we have a django app which uses django log, and we needs to run more than one
instance of this application, there would be a problem that log file will not work well
as all the instances write logs into the same file. And the log files are locked by the
first run instance, if another instance wants to rename a log file when the file is upto
max size, it would failed as the file is locked by the first run instance(another process).

Way to solve the problem:

1. Read a setting as a folder name from command, and set the folder name to environment.

    manage.py
    ---
    if __name__ == "__main__":
        ...
        ...
        for arg in sys.argv:
            if arg.startswith('--sub-logdir='):
                os.environ.setdefault("SUB_LOG_DIR", arg.split('=')[1])
                sys.argv.remove(arg)
        ...
        ...

2. In django settings.py file, read the sub folder and append it to read log path.

    settings.py
    ---
    _SUB_LOG_DIR = os.environ.get('SUB_LOG_DIR', '')
    _LOG_FILE = lambda f: os.path.join(BASE_DIR, '_log', _SUB_LOG_DIR, f)

    LOGGING = {
        ...
        'handlers': {
            'foo': {
                ...
                'filename': _LOG_FILE('django.log'),
                ...
            }
        }
        ...
    }

3. Run in shell like this:

    python manage.py runserver --sub-logdir=instance1-folder
    python manage.py runserver --sub-logdir=instance2-folder

# Converting string--bytes in different languages

Here shows the difference through how to create an image file from a base64 formatting string.

## python

    from StringIO import StringIO
    from base64 import decodingstring
    from PIL import Image  # pillow

    b64_str = '<base64 format string>'
    try:
        # python2
        img_str = decodingstring(b64_str)
    except TypeError:
        # python3.x
        # Calling encode() to convert to a bytes object first.
        img_str = decodingstring(b64_str.encode())
    img = Image.open(StringIO(img_str))
    img.save('foo.png')

## csharp

	using System;
	using System.Drawing;
    using System.IO;

	string b64Str = "<base64 format string>";
	byte[] imgBytes = Convert.FromBase64String(b64Str);
	Image img = Image.FromStream(new MemoryStream(imgBytes));
	img.Save("foo.png");

# Extends django models in the non-models-owner-app

In order by reduce coupling, we can define models in app fooapp_a and extends
the models in another app named fooapp_b. Suppose we have a project like this.

    django-project
    - fooapp_a
      - models.py
      - views.py
    - fooapp_b
      - extends.py
      - views.py

**Here is the implement of the extension**

fooapp_a/models.py

    class Person(<django_models.Model>):
        name = models.CharField()
        age = models.IntegerField()

fooapp_b/models.py

    from fooapp_a.models import Person

    @ext(Persion)
    def tell_age(person):
        return 'My name is %s, and my age is %d' % (person.name, person.age)

**In the source above we used a decorator to extend the models.**

    def ext(model, attr_name=None):
        def _ext(func):
            name = attr_name if attr_name else func.__name__
            if getattr(model, name, None):
                raise AttributeError(
                    "Model '%s' already has attribute '%s'" % (model.__name__, name)
                )
            setattr(model, name, func)
        return _ext
