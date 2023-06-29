from guizero import *
app = App(title="Currancy convert")
def Convertion_output():
    if Option == "USD - EUR":
        output = convert_input * 1
    elif Option == "EUR - USD":
       output = convert_input / 1
    
Message1 = Text(app, text="choose you convertion")
Option = ButtonGroup(app, options=["USD - EUR", "EUR - USD"])#, "EUR - GBP",
#"GBP - EUR", "GBP - USA", "USA - GBP"], selected="GBP - EUR")
#
#
message2 = Text(app, text="enter the amount you wish to convert")
convert_input = TextBox(app)
#
#
btn_convertion = PushButton(app,text='Convertion', command= Convertion_output)
#
#
app.display()
