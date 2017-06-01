# run django command in jupyter [ref](https://andrewbrookins.com/python/using-ipython-notebook-with-django/)

    pip install jupyter
    pip install django-extensions
    python ./manage.py shell_plus --notebook

# ironpython

document

> http://ironpython.net/
> https://ironpython-test.readthedocs.io/en/latest/contents.html

source

> https://github.com/IronLanguages/main
> http://ironpython.codeplex.com/

usage:

> http://stackoverflow.com/questions/7053172/how-can-i-call-ironpython-code-from-a-c-sharp-app
> http://www.cnblogs.com/yhyjy/archive/2012/09/10/2678472.html
> http://blog.csdn.net/baliguan163/article/details/8520113


# pillow common usage

## conversion in different data format(without file system storage)

*base64 to pillow image*

    from cStringIO import StringIO
    from PIL import Image
    from base64 import b64decode

    b64_img_string = `some img data in base64 data format`
    buf = StringIO(b64decode(b64_img_string))
    img = Image.open(buf)

*pillow image to base64*

    from cStringIO import StringIO

    img = `some pillow image object`
    buf = StringIO()
    img.save(buf, format='JPEG')
    img_string = buf.getvalue()
