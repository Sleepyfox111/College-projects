from guizero import *

app = App(title="texteditor")#, width =1500, bg= "black")
def open_file():
    #this reads from the file when the open button is pressed
    with open(file_name.value, "r") as f:
        editor.value = f.read()
        #
def save_file():
    #this is the function that write to the file when the save button is pressed
    with open(file_name.value, "w") as f:
        f.write(editor.value)
        #
def change_font():
    editor.font = font.value
#
def change_text_size():
    editor.text_size = size.value
def Exit():
    app.destroy()
#
def file_function():
    print("file options")
    #
def edit_function():
    print("Edit option")
    #
file_controls = Box(app, align="top", width="fill")
#
file_name = TextBox(file_controls, text="text_file.txt", width=50,
align="left")
#
save_button = PushButton(file_controls, text="Save", align="right", command =save_file)
#this creates and alighnt the save pushbutton and then runs the function with the command.
#
open_button = PushButton(file_controls, text="Open", align="right", command =open_file)
#
#
editor = TextBox(app, multiline=True, height="fill", width="fill")
#
#
preferences_controls = Box(app, align="bottom", width="fill", border=True)

font = Combo(preferences_controls, options=["courier", "times new roman",
"verdana","comic sans"], align="left", command=change_font)
Exit = PushButton(preferences_controls, text="exit", align="right", command=Exit)
#
#
size = Slider(preferences_controls, align="left",
command=change_text_size, start=10, end=45)
#
#
editor.resize(1, 1)
editor.resize("fill", "fill")
#
#
Menubar=MenuBar(app,toplevel=["File","Edit"], options=[[["File option 1",file_function], ["File option 2",file_function]],
                                                      [["Edit option 1", edit_function],["Edit option 2", edit_function]]])
#
#
#
app.display()
