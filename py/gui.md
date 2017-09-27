# Create simple Gui application with python

## create app with python scripts

    # simple-app.py
    from datetime import datetime
    import Tkinter

    class Timeman(object):
        def init_form(self):
            self.form = Tkinter.Tk()
            self.form.title('simple app')

            self.ipt_area = Tkinter.Entry(self.form, width=30)
            self.display_info = Tkinter.Listbox(self.form, width=50)
            self.button = Tkinter.Button(self.form, command=self.append_datetime_now, text='Print Hello')

            self.ipt_area.pack()
            self.display_info.pack()
            self.button.pack()

        def append_datetime_now(self):
            self.display_info.insert(0, datetime.strftime(datetime.now(), '%Y-%m-%d %H:%M:%S'))

    timeman = Timeman()
    timeman.init_form()
    Tkinter.mainloop()

## pack to exe

    pip install pyinstaller

    pyinstaller --onefile ./simple-app.py
