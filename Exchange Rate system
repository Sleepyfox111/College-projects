####################
####################
####################
import pandas as pd # this is the import pandas this brings the pandas into be able to be used in the chart
import matplotlib as m # this is the matplotlib import allowing us to create charts 
import matplotlib.pyplot as m#this allow the matplotlib command to be ploted
import time as t# this is a time import that allow us to determant how quickly it moves on
import csv# this bring the csv file in to be able to be split and striped ready for uses
import hashlib# this is to allow the password to be hashed
###################
###################   ███████████
###################   ██       ██
def startMenu():
    # this is the start Menu this is what the reader will first see on loading the code
    print("=================================")
    print("*            Welcome            *")
    print("*  i am your exchange rate bot  *")
    print("*     i will assist you in      *")
    print("*    exchaning your currancy    *")
    print("*   lets move on to the Login   *")
    print("=================================")
    t.sleep(2)
def login():
    # this is the login part of the code where the user can login and start there exchange
    # to keep it safe from potsecial hacker there are a limited amount of attemps before you have restart the code
    #Username = Josh
    #Password = qwerty
    count = 3# this gives the user a certain amount of goes before kicking them off this stop people from brute force attacks
    for i in range(3):#this will reaped the code till the correct username and pasword is put in
        username = input("please enter username\n")
        if username.isalpha() == True: # this makes sure that input from the user is a in the aplha bet and not numbers this prevents crashes
            with open("User.Txt", "r") as f:#this opens the file and closes the file this saves space in ram and extra line of code
                User = f.read()
                User = User.split(",")#this remove any commas in the file
                name = User[0]# this check that the input of the user is the same as the username in the file
                ppasw = User[1]# this make sure the password is the same as the user put in compared to the file
                if username == name:
                    ppass = input("put in your password\n")
                    ppass = hashlib.sha512(ppass.encode('utf8')).hexdigest()#this is to check the hashed password is correct. this is because the password is stored hash to stop attackers from being able to login as the person whos password it is
                    if ppass == ppasw:#checks the password put in is the same as the password in teh file
                        print("Username and Password Correct Forwarding you to the Main menu. Please")
                        return True
        else:
            print ("username or password is wrong.")# this tells them that the user name and password 
        count -= 1
        print("username or password is wrong.")
        print("you have" , count, "go left")# this tells them how many goes they have left 
    else:
        print("you have no more attemps") #if they run out of goes this message will be displayed telling them they have no goes left
def fileExtract():
    #this is where the file get split and turned to seprater file data and rates.
    #this means later we can call on them to uses in calculetions
    dates = []#lists the date is stored in
    rates = []#what the rate is stored in to be used later

    with open("USDtoGBP.csv",'r') as data: # this opens and closes the file.
        for line in csv.reader(data):
            if line[0] != "Date":# this is telling the code to skip the first line of code as its not relevent to the caculations
                dates.append(line[0])
          
                line[1] = float(line[1])# this turn the list rates in to a float this stops crashes from occuring later when trying to calcualate
                rates.append(line[1])
                rate = rates[0]
    data.close()
    return rate
#
#      
def Menu():
    # this is the main Menu where the user can choose what they would like to do
    print("=================================")
    print("*  1 = Graph on GBP to USD      *")
    print("*  2 = Graph on USD to GBP      *")# this print the menu telling the person the options
    print("*  3 = Convertion of GBP to USD *")
    print("*  4 = Convertion of USD to GBP *")
    print("=================================")
    Option = "0"
    while Option != "1" and Option != "2" and Option != "3" and Option != "4": # this makes sure the user puts in one of these number and not other values
        Option = input("what would you like to do. Please enter a number between 1 and 4\n")
        if Option == "1":
            print("you will now be take to the Graph of GBP to USD.")# if this option is chosen it will take them to the graph of GBP to USD
            print("when you are done please close the window.")# this tell the user after they have finished with the graph 
            return GraphGBPtoUSD()
            t.sleep(2)
        if Option == "2":
            print("you will now be take to the Graph of USD to GBP")# this will take them to the USD to GBP graph 
            print("when you are done please close the window.")
            return GraphUSDtoGBP()
            t.sleep(2)
        if Option == "3":
            print("you will now be take to the USD to GBP convertion")
            return GBPtoUSD()#this takes it to the convertion GBP to USD
            t.sleep(2)
        if Option == "4":
            print("you will now be take to the USD to GBP")
            return USDtoGBP()#this takes them to the USD To GBP
            t.sleep(2)
        else:
            Option = input("what would you like to do. Please enter a number between 1 and 4\n")# if the user does not put in one of the value they will be met by this message
#
#
def USDtoGBP():
    # this is the function that will convert the USD to GBP 
    rates = fileExtract()# this tell the code to grab the numbers from the we extraced earlyer
    convert = input("please enter the amount you would like to convert\n$")
    valid = True
    for char in convert:
        if char.isnumeric() == False and char !=".": #this makes sure the input is a number this prevents people putting letters in and crashing the code
            valid = False
    if convert == ".":#this allows the user to put in decimals so if they need a more exact number the code will not crash
        valid = False
    while valid == False: # if the user does not enter a number they will be displayed this messages
        print("please reenter the value")
        convert = input("please enter the amount you would like to convert/n$")# this is a reapted of the top to allow the user to enter an new value
        valid = True
    #for char in convert:
    #    if char.isnumeric() == False and char !=".":#check to see if its a number
    #        valid = False
    #if convert == ".":
    #    valid = False
    convert = float(convert)# this converts it is a float so if its a decimal it is able to be calcualated.
    amount = convert * rates# this does the math from the file which make sure the figue is allways up to date
    print("The amount is: £{:.2f}".format(amount))#this formats it and then prints it out to two decimal places
    return End()
#
#
def GBPtoUSD():
    # this is the same as the USD to GBP however it converts it the other way.
    rates = fileExtract()
    convert = input("please enter the amount you would like to convert\n£")
    valid = True
    for char in convert:
        if char.isnumeric() == False and char !=".":#check to make sure its a number.
            valid = False# if it comes back false it will dispay an error message and ask them to reenter the value.
    if convert == ".":
        valid = False
    while valid == False:# this is where the error message will be dispayed.
        print("please reenter the value")
        convert = input("please enter the amount you would like to convert/n£")
        valid = True
    for char in convert:
        if char.isnumeric() == False and char !=".": #checks to make sure the value is a number.
            valid = False
    if convert == ".":
        valid = False
    convert = float(convert)#converts it to a float ready to be calculated
    amount = convert / rates#does the caculation
    print("The amount is: ${:.2f}".format(amount))#prints it and displays it to two decimal places
    return End()
#
#
def GraphGBPtoUSD():
    #this is the graph section of the code this if the user requests will dispay the trend of GBP to USD and how the exchange rate goes up and down
    currency = pd.read_csv('USDtoGBP.csv', parse_dates=['Date'])
    currency['USD'] = 1/currency['GBP']# this converts it to the GBP graph rather that USD graph 
    m.xlabel('Date', fontsize=12)# this displays the correct title of the graph
    m.xticks(rotation=90) #this rotates it so it can be read
    m.plot(currency['Date'], currency['USD']) # 
    m.title('GBP to USD over time') # this is the title of the graph so it tells the user what one there looking at
    m.ylabel('Exchange Rates', fontsize=12)# this label the y axis 
    m.xticks(rotation=90) # this rotates it 90 degrees 
    m.show() # this then prints the graph of and shows them 
    return End()
#
#
def GraphUSDtoGBP():
    currency = pd.read_csv('USDtoGBP.csv', parse_dates=['Date'])# this find the file and put it in the graph
    m.xlabel('Date', fontsize=12)# this displays the correct title of the graph
    m.xticks(rotation=90)# turn it 90 degrees
    m.plot(currency['Date'], currency['GBP'])# this plots the graph 
    m.title('USD to GBP over time') # this is the title 
    m.ylabel('Exchange Rates', fontsize=12) # this lable the y axis 
    m.xticks(rotation=90) 
    m.show()# this show the graph
    return End()
#
#
def End():

    #this is the end function this gets dispayed at the end of every function
    begin = input("is there anything else you would like to do Y/N\n")# this gives them the option to do another convertion or view a graph
    while True:# this makes it so they have to put in a value
        if begin == "Y":#this will take them back to the main menu
            print("returning you to main menu")
            return Menu()
        else:# an else statment is uses insted of a elif because in mean anything else they put in will take them out
            print("we hope to see you again soon")
            quit()
#
#

#########################
#       Main code       #
#########################
# this is the main code where it starts and ends the code
startMenu()# this is the take you to the start menu 
Vauthorised = login() # if you login correctly then you will be able to accses all of the menus 
if Vauthorised == True:
    Menu()
    if Menu == "GBPtoUSD()":# this takes you to GBPtoUSD convertion
        End()
    #
    #
    if Menu == "USDtoGBP()":# this takes you to USD to GBP convertion
        End()
    #
    #
    if Menu == "GraphGBPtoUSD()": # this take you to the Graph
        End()
    #
    #
    if Menu == "GraphUSDtoGBP()": # this take you to the graph
        End()
