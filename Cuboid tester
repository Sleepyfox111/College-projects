from guizero import *
def Calc():
    if Height.value.isdigit()==False or Width.value.isdigit()==False:
        error(title="wrong input", text ="You must type in numbers for height and width")

    elif not Depth.value.isdigit() and Depth.value != "":
        error(title="wrong input", text ="You must type in a number for depth")
    else:
        Area = int(Height.value) * int(Width.value)
        if Depth.value =="":
            Result.value = str(Area)
        else:
            volume = Area*int(Depth.value)
            Result.value = str(volume) + ""



app = App(title ="calculator", layout="grid")
#
text = Text(app, text="Height", grid=[0,0], align="left")
Height = TextBox(app, grid=[1,0], align="left",width="25")
#
text = Text(app, text="Width", grid=[0,1], align="left")
Width = TextBox(app, grid=[1,1], align="left", width="25")
#
text = Text(app, text="Depth", grid=[0,2], align="left")
Depth = TextBox(app, grid=[1,2], align="left",width="25")

button = PushButton(app, text="calculate", grid=[1,5], command=Calc)

result = Text(app, text="result", grid=[0,6], align="left")
Result = Text(app, text=" ", grid=[1,6], align="left")

app.display()
