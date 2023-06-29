import csv # this bring the file to the program. this allow it to access all the location that the computer can read from the file.
import webbrowser # this pull the webbrowser in to the code allowing it to be launch with the hit of the enter key
# username: Josh
# password: qwerty
###################################################
##          Begining of Def Statament            ##
###################################################
def Welcome():
    #this is the welcome proceder this is what will allow the user to log in and start to choses the options that they want to eat
    print("+---------------------+")
    print("|                     |")
    print("|        Welcome      |")
    print("|   My Name is Roger  |")
    print("|                     |")
    print("+---------------------+")
    #login()
    #this shows a welcome mesasge befor they login.
    #this give charater before they login insted of them looking at a login screem
#
#
def login():
    #this is a function.
    #this is the login page where the user puts in a pre stored user name and password 
    names = input("put in your username\n")
    if names.isalpha() == True:
        names = str(names)
        with open("Name.txt","r") as f:#this opens the txt file where the username and password is store this give it a samll amount of security.
            Name = f.read()
            Name = Name.split()
            pname = Name[0]# this tell the computer where in the file the username and password is stored
            ppasw = Name[1]
            if names == pname:
                ppass = input("put in your password\n")
                if ppass.isalpha() == True:#this checks that the username and password is in the alphabet this prevents people from crashing the code by putting numbers in
                    if ppass == ppasw:
                        print("access Granted")
                        return True
    else:
        return False
#
#
def food():
    #this is a function where the custmer choises there food.
    #it will returen indian, restraunt or fast food
    # they have three choises of food
    print("+---------------------+")
    print("|     1. indian       |")
    print("|                     |")
    print("|     2. restaurant   |")
    print("|                     |")
    print("|     3. fast food    |")
    print("+---------------------+")
    foods = "0"
    while foods != "1" and foods != "2" and foods != "3":#this will loop the code until the user puts in a valid option.
        foods = input("please put in your food option. put in a number from 1-3\n")
        if foods == "1":
            return "indian"
        elif foods == "2":
            return "restaurant"
        elif foods == "3":
            return"fast food"
        else:
            foods = input("please put in your food option. put in a number from 1-3\n") #this make the code loop if the three option are not chosen.
#
#
def budget():
    #this a function where the user choises there budget
    #it will returen £0-10, £10-15 £15+
    # the budget allows the user to pick how much they want to spend
    print("+---------------------+")
    print("|     1. £0-£10       |")
    print("|                     |")
    print("|     2. £10-£15      |")
    print("|                     |")
    print("|     3. £15+         |")
    print("+---------------------+")
    budget = "0"
    while budget != "1" and budget != "2" and budget != "3":#this make the user choise one of the three option of they dont then the code will loop back round and they need to choise again
        budgets = input("please put in your budget option. put in a number from 1-3\n")
        if budgets == "1":
            return "£0-£10"
        elif budgets == "2":
            return "£10-£15"
        elif budgets == "3":
            return "£15+"
        else:
            budgets = input("please put in your budget option. put in a number from 1-3\n")
 #
 #
def location():
    #this is a funcation where the user choises where they wnat there food from.
    #it will returen portmouth, littlehampton and havant.
    print("+---------------------+")
    print("|   1. portsmouth     |")
    print("|                     |")
    print("|   2. littlehampton  |")
    print("|                     |")
    print("|   3. havant         |")
    print("+---------------------+")
    Locations = "0"
    while Locations != "1" and Locations != "2" and Locations != "3":
        Locations = input("please put in your location option. put in a number from 1-3\n")
        if Locations == "1":
            return "portsmouth"
        elif Locations == "2":
            return "littlehampton"
        elif Locations == "3":
            return"Havant"
        else:
            Locations = input("please put in your location option. put in a number from 1-3\n")


def findrestaurant(foodchoice, budgetchoice, locchoice):
    #this precedure takes all the past three option and the choises the user has chosen.
    #it then goes in to the csv file that has been imported at the top and will scan the file for the restaraunt that the user has pick.
    location = locchoice
    food = foodchoice
    budget = budgetchoice
    with open("resttest.csv","r") as file:#this open the CSV file and gets it ready to show the most sutibale restraunt
        Flag = False
        for line in file:
            rec = line.strip().split(",")
            if location == rec[1] and food == rec[2] and budget == rec[4]: # this will go to the file and compair what you have put in to the file and out put the most sutible option.
                print(rec[0] + " " + rec[5])# this print statment will print the name and the url of the restaunt
                url = rec[5]
                input("press any key to go to website")# this just tell the user to launch the website they have to press enter
                webbrowser.open(url, new = 0, autoraise = True)#this section of code is uses to launch the website it take them to the website if possible
                Flag = True
        if Flag == False:
            print("not able to find a sutible location")
            
#

#

##################################################
#                                                #
#                   MAIN CODE                    #
#                                                #
##################################################
#this is the main part of the code where they are called from this make is much simplar as it doesn't requier loads of if statments in if statment to run. 
##it also means if the code breaks it simple to fix as there is limited places for it to crash
Welcome()
Vauthorised = login()
if Vauthorised == True:
    foodchoice = str(food())
    budgetchoice = str(budget())
    locchoice = str(location())
    findrestaurant(foodchoice, budgetchoice, locchoice)
else:
   print("we are unable to find your account.")
