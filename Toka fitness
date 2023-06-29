from guizero import *  #window is second form
import sqlite3
#from sqlite3 import Error
#import mysqlx
#Import SQL
import os
import os.path
#Import datetime
import datetime
import hashlib
import webbrowser
import matplotlib.pyplot as plt
import pandas as pd
from datetime import datetime # for strptime()

sql = """
CREATE TABLE "UserTbl" ( 
"UserID" INTEGER NOT NULL,
"Username" TEXT,
"Password" TEXT,
"Fname" TEXT,
"Sname" TEXT,
"Email" TEXT,
"Phonenumber" TEXT,
"DofB" DATE,
"Card_details" STRING,
"CVV" STRING,
PRIMARY KEY("UserID" AUTOINCREMENT)
);
CREATE TABLE "Extra_Deatails" (
"ExtraID"  INTEGER NOT NULL,
"Height" STRING,
"Weight" INTEGER,
"Dateofweight" INTEGER,
"UserID"  INTEGER,
PRIMARY KEY("ExtraID" AUTOINCREMENT),
CONSTRAINT "UserID_fk"  FOREIGN KEY("UserID") REFERENCES "UserTbl"("UserID")
);
insert into UserTbl (Username, Password, Fname, Sname, Phonenumber, Email, DofB, Card_details, CVV) values ('Tester','5b722b307fce6c944905d132691d5e4a2214b7fe92b738920eb3fce3a90420a19511c3010a0e7712b054daef5b57bad59ecbd93b3280f210578f547f4aed4d25', 'Josh', 'bob', '12345678901', 'Josh@gmail.com', '20/12/2066', '1234567890123456', '760');
insert into UserTbl (Username, Password, Fname, Sname, Phonenumber, Email, DofB, Card_details, CVV) values ('User','5b722b307fce6c944905d132691d5e4a2214b7fe92b738920eb3fce3a90420a19511c3010a0e7712b054daef5b57bad59ecbd93b3280f210578f547f4aed4d25', 'user', 'Redacted', '12345678901', 'Raven@gmail.com', '12/12/1066', '9999999999999999', '999');

insert into Extra_Deatails (Height, Weight, Dateofweight, UserID) values ('6.1', '65', '29/11/2022' ,1);
insert into Extra_Deatails (Height, Weight, Dateofweight, UserID) values ('6.1', '70', '2/12/2022' ,1);

insert into Extra_Deatails (Height, Weight, Dateofweight, UserID) values ('5.6', '60', '30/11/2022' ,2);
insert into Extra_Deatails (Height, Weight, Dateofweight, UserID) values ('5.6', '65', '3/12/2022' ,2);
"""
#
#Global variables here
#
#
database_file = 'Fitness.db'
LoggedIn_ID = 1 # store customerID when logged in

#
#
#
#Delete the database if it exists
#
#
if os.path.exists(database_file):
	os.remove(database_file)
#
#Connect to the database
conn = sqlite3.connect(database_file) #My connection is called 'conn'
#Get a cursor pointing to the database
cursor = conn.cursor()
#Create the tables
cursor.executescript(sql) # creates from DDL above, script more than 1 command
#Commit to save everything
conn.commit()
#Close the connection to the database
#
#Queries the database using the database parameter as the database
#to query and the query parameter as the actual query to issue
# for SELECT
#
def query_database(database, query):
	Lconn = sqlite3.connect(database)
	cur = Lconn.cursor()			# use a local cursor called cur
	cur.execute(query)
	rows = cur.fetchall()
	cur.close()
	return rows
#
#
#Executes the sql statement to INSERT and UPDATE rows
#
def execute_sql(database, sql_statement):
	Lconn = sqlite3.connect(database)
	cur = Lconn.cursor()
	cur.execute(sql_statement)
	Lconn.commit()
	return cur.lastrowid
##################################################################
def Login():
	# this will show the user a loggin window and hide the menu
	app.hide()
	signup.hide()
	login.show()
	Main_App.hide()
	#
def Pass_reset():
	PW_change.show()

def Change_PW():
	global LoggedIn_ID
	if New_PW.value == "":
		info("Error", "Please enter a new password")
	elif Change_Uname.value == "":
		info("Error", "Enter you username")
	#elif Change_Email.value == "":
		#info("Error","Enter your Email")
	else:
		name = Change_Uname.value
		sqlselect = "SELECT * FROM UserTbl WHERE Username = '"+name+"'"
		rows = query_database(database_file, sqlselect)
		#if len(rows) == 0: ### This checks that the user was found ###
		#else:
		LoggedIn_ID = rows [0][0]
		New_pw = New_PW.value
		New_Pass = hashlib.sha512(New_pw.encode('utf8')).hexdigest()
		UpdateDataSQL = "UPDATE UserTbl SET Password = '"+str(New_Pass)+"' WHERE UserID = '"+str(LoggedIn_ID)+"'"
		info("Sucsess", "your password has been changed")
		execute_sql(database_file, UpdateDataSQL)
		PW_change.hide()
def Exit():
	# when exit is pressed it ends the program
	app.destroy()
#
#
def Signup():
	# show to user a sign up window to allow them to create an account
	app.hide()
	login.hide()
	signup.show()
	############
def Back():
	#this allow the user to go back from the page they are on and take them back to the main menu
	login.hide()
	signup.hide()
	Main_App.hide()
	app.show()
	###############

def Cancel():
	#this close the password change incase they miss cliked
	PW_change.hide()
	#######
def main():
	# this shows the main app where the user can choose what they want to do
	Main_App.show()
	#####
	# this hide the the main feature of the menu and the login system
	login.hide(); height_txt.hide();weight_txt.hide()
	blank1.hide(); Height.hide(); Weight.hide()
	########
	#this is hide every thing on the page
	Calculate.hide(); Next.hide(); Back.hide()
	Learn_more.hide(); F_Next.hide(); Fadvice3.hide()
	F_Back.hide(); More_recipes.hide(); Back_workout.hide()
	Chest.hide(); Biceps.hide(); Legs_work.hide()
	Cardio.hide(); Text_blank.hide(); Leader.hide()
	################

def BMI_calc():
	# this show the nesscary box for the BMI caculator
	height_txt.show(); weight_txt.show(); blank1.show()
	Height.show(); Weight.show(); Calculate.show()
	#############
	#this makes sure every this is hidden in case they came from another tab
	advice1.hide(); advice2.hide(); advice3.hide()
	advice4.hide(); advice5.hide(); advice6.hide()
	#
	Next.hide(); Back.hide(); Learn_more.hide()
	F_Next.hide(); Fadvice1.hide(); Fadvice2.hide()
	Fadvice3.hide(); F_Back.hide(); More_recipes.hide()
	Back_workout.hide(); Chest.hide(); Biceps.hide()
	Legs_work.hide(); Cardio.hide(); Text_blank.hide()
	Leader.hide(); Fadvice4.hide(); Leader.hide()
	Logo_menu.hide()

def Workout_advice():
	#this show all the first image for workout advice
	advice1.show()
	#####
	#this makes sure every this is hidden in case they came from another tab
	height_txt.hide(); weight_txt.hide(); blank1.hide()
	Height.hide(); Weight.hide(); Calculate.hide()
	Next.show(); advice2.hide(); advice3.hide()
	#
	advice4.hide(); Back.hide(); Learn_more.hide()
	F_Next.hide(); Fadvice1.hide(); Fadvice2.hide()
	Fadvice3.hide(); F_Back.hide(); More_recipes.hide()
	Back_workout.hide(); Chest.hide(); Biceps.hide()
	Legs_work.hide(); Cardio.hide(); Text_blank.hide()
	Leader.hide(); Fadvice4.hide(); Leader.hide()
	Logo_menu.hide()

def Next_image():
	# this allows the user to go though the images without having to open a new window
	if advice1.visible == True:
		advice2.show()
		advice1.hide()
		Back.show() 
	elif advice2.visible == True:
		advice3.show()
		advice2.hide()
	elif advice3.visible == True:
		advice4.show()
		advice3.hide()
	elif advice4.visible == True:
		advice5.show()
		advice4.hide()
	elif advice5.visible == True:
		advice6.show()
		advice5.hide()
		Learn_more.show(); Next.hide()

def Back_image():
	#this go back from the image they are on
	if advice2.visible == True:
		advice1.show()
		advice2.hide()
		Back.hide() 
	elif advice3.visible == True:
		advice2.show()
		advice3.hide()
	elif advice4.visible == True:
		advice3.show()
		advice4.hide()
	elif advice5.visible == True:
		advice4.show()
		advice5.hide()
	elif advice6.visible == True:
		advice5.show()
		advice6.hide()
		Next.show(); Learn_more.hide()
		# 
def Food_recipes():
	# this show the first image for food recipy
	Fadvice1.show(); F_Next.show();F_Back.hide()
	############
	advice1.hide(); advice2.hide(); advice3.hide()
	advice4.hide(); advice5.hide(); advice6.hide()
	height_txt.hide(); weight_txt.hide(); Calculate.hide()
	#this makes sure every this is hidden in case they came from another tab
	blank1.hide(); Height.hide(); Weight.hide()
	Next.hide(); Back.hide(); Learn_more.hide()
	Fadvice2.hide(); Fadvice3.hide()
	Back_workout.hide(); Chest.hide(); Biceps.hide()
	Legs_work.hide(); Cardio.hide(); Text_blank.hide()
	Leader.hide(); Fadvice4.hide(); Leader.hide()
	Logo_menu.hide()
	#
def FNext():
	#this allow them to scroll to the next image
	if Fadvice1.visible == True:
		Fadvice2.show()
		Fadvice1.hide()
		F_Back.show()
	elif Fadvice2.visible == True:
		Fadvice3.show()
		Fadvice2.hide()
	elif Fadvice3.visible == True:
		Fadvice4.show()
		Fadvice3.hide()
		F_Next.hide(); More_recipes.show()
##########
def FBack():
	#this allows them to scroll back from a current image
	if Fadvice2.visible == True:
		Fadvice1.show()
		Fadvice2.hide()
		F_Back.hide()
	elif Fadvice3.visible == True:
		Fadvice2.show()
		Fadvice3.hide()
	elif Fadvice4.visible == True:
		Fadvice3.show()
		Fadvice4.hide()
		F_Next.show(); More_recipes.hide()
def Social_media():
	return webbrowser.open('https://www.puregym.com/app/')
def Custom():
	#this is for the custom workouts which show the option the user can pick
	Legs_work.show(); Chest.show(); Biceps.show()
	Cardio.show(); Back_workout.show(); Text_blank.show()
	###
	#this makes sure every this is hidden in case they came from another tab
	advice1.hide(); advice2.hide(); advice3.hide()
	advice4.hide(); advice5.hide(); advice6.hide()
	Next.hide(); Back.hide(); Learn_more.hide()
	F_Next.hide(); Fadvice1.hide(); Fadvice2.hide()
	Fadvice3.hide(); F_Back.hide(); More_recipes.hide()
	login.hide(); height_txt.hide();weight_txt.hide()
	blank1.hide(); Height.hide(); Weight.hide()
	Calculate.hide(); Leader.hide();Fadvice4.hide()
	Leader.hide(); Logo_menu.hide()
def Cookies():
	#this is for the cookies window hiding the extra info till the user asks
	Cookie.show()
	Ness.hide(); Ness_content.hide()
	Functional_cont.hide(); Functional.hide()
	Statistical.hide(); Statistical_cont.hide()
	Marketing_cont.hide(); Marketing.hide()
	hide_cookie.hide(); More_cookie.show()
	Accept.show(); Accept_Chosen.hide()

def Manage_cookies():
	#this show the extra info is the user wants
	Ness.show(); Ness_content.show()
	Functional_cont.show(); Functional.show()
	Statistical.show(); Statistical_cont.show()
	Marketing_cont.show(); Marketing.show()
	hide_cookie.show(); More_cookie.hide()
	Accept.hide(); Accept_Chosen.show()

def hide_cookies():
	#this then hide it after the user pick what they want
	Ness.hide(); Ness_content.hide()
	Functional_cont.hide(); Functional.hide()
	Statistical.hide(); Statistical_cont.hide()
	Marketing_cont.hide(); Marketing.hide()
	hide_cookie.hide(); More_cookie.show()
	Accept.show(); Accept_Chosen.hide()

def Leg_workouts():
	# this show the leg exasize window
	Leg.show()

def Next_Exercises():
	#this allow them to move to the next exasize
	if Squats.visible == True:
		Leg_Back.show()
		Squats.hide();Exercises1.hide();Exercises1_reps.hide()
		Deadlift.show();Exercises2.show();Exercises2_reps.show()
	elif Deadlift.visible == True:
		Leg_Next.hide()
		Deadlift.hide();Exercises2.hide();Exercises2_reps.hide()
		Exercises3_reps.show(); Exercises3.show();Bulgarian.show()

def Back_Exercises():
	#this allow the user to scroll back on the to see the previos exasize
	if Deadlift.visible == True:
		Leg_Back.hide()
		Squats.show();Exercises1.show();Exercises1_reps.show()
		Deadlift.hide();Exercises2.hide();Exercises2_reps.hide()
	elif Bulgarian.visible == True:
		Deadlift.show();Exercises2.show();Exercises2_reps.show()
		Exercises3_reps.hide(); Exercises3.hide();Bulgarian.hide()
		Leg_Next.show()

def chest_workouts():
	#show chest window
	chest.show()
	##
def Chest_Next():
	#allows the user to scroll though the exasizes
	if Bench.visible == True:
		Back_Chest.show()
		Exercises1.hide();Bench.hide();Exercises1_reps.hide()
		Chress_Press.show();Exercises2.show();Exercises2_reps.show()
	elif Chress_Press.visible == True:
		Next_chest.hide()
		Exercises3_reps.show(); Exercises3.show(); Cable.show()
		Chress_Press.hide();Exercises2.hide();Exercises2_reps.hide()

def Chest_Back():
	# lets the user see the previose exasize
	if Chress_Press.visible == True:
		Back_Chest.hide()
		Exercises1.show();Bench.show();Exercises1_reps.show()
		Chress_Press.hide();Exercises2.hide();Exercises2_reps.hide()
	elif Cable.visible == True:
		Chress_Press.show();Exercises2.show();Exercises2_reps.show()
		Exercises3_reps.hide(); Exercises3.hide(); Cable.hide()
		Next_chest.show()

def Under_construction():
	#for the tabs that are still being made
	info("Error", "Coming Soon")
###############
def do_this():
	#this check to see if the user has tick the T&C
	if Terms.value == 1:		
		info("Terms and conditions", "1.This agreement commences once you have indicated your acceptance in the Declaration section of the web sign up process.\n 2.This agreement will become binding on you and us when we contact you to confirm your membership application has been accepted, at which point a contract will come into existence between you and us.\n 3.You will be entitled to all the rights and privileges set for the Type of Membership chosen.\n 4.You cannot transfer this agreement to anyone else")
		signup_button.enable()
		# makes the accsept
	else:
		info("Error", "you must accept Terms and conditions")

###
def WorkoutLearnMore():
	#opens a website if the user want to know more
	return webbrowser.open('https://www.puregym.com/')

def Learn_More_recipes():
	#opens a website if the user want to know more
	return webbrowser.open('https://www.hellofresh.co.uk/menus')

def Dark_Mode():
	#this is for accsessiblity for the user incase they struggle to see on a white back round
	app.bg = "#434343"
	app.text_color = "#eef2f3"
def Light_Mode():
	#this is for accsessiblity for the user incase they struggle to see on a Black back round
	app.bg = "#eef2f3"
	app.text_color = "#434343"
	#####################
def Zoom():
	#lets the user zoom in
	Size.show()
	Zoom_confirm.show()
	#
def Zoom_Percent():
	#make the size apply to all windows
	app.text_size = Size.value
	#
def Size_confirm():
	#make the size slide dispear
	Size.hide()
	Zoom_confirm.hide()
	#
def courier():
	#change the font
	app.font = "courier"
	#
def Roman():
	#change the font
	app.font = "times new roman"
	#
def verdana():
	#change the font
	app.font = "verdana"
	#
def comic():
	#change the font
	app.font = "comic sans"
######################################
def PREM():
	#for user that try to uses premium features
	if Custom_Workout.enabled == False:
		info('Error', 'You need Premium')
	elif Social.enabled == False:
		info('Error', 'You need Premium')
	elif BMI_cal.enabled == False:
		info('Error', 'You need Premium')

def Buy():
	Purchase.show()

def confirm():
	#this allow the user to have an account that has accsess to premium
	#
		#check to make sure all inputs field have been ented and are valid
	if Num_Card.value == "":
		info("Error","you must enter card Numbers")
	elif Num_Card.value.isnumeric() == False:
		info("Error", "Please make sure there are only digits")
	elif len(Num_Card.value) != 16:
		info('Error!','Please enter the correct length of digits in the CreditCard textbox')
	elif CVV_Num.value == "":
		info("Error","you Must Enter Your CVV Numbers")
	elif CVV_Num.value.isnumeric() == False:
		info("Error", "Please make sure there are only digits")
	elif len(CVV_Num.value) != 3:
			info('Error!','Please enter the correct length of digits in the CVV textbox')
	else:
			#exacute the update statment updating there accont giving them premium
		sql_update = "UPDATE UserTbl SET Card_details=%s, CVV=%s WHERE UserID=%s" % (Num_Card.value, CVV_Num.value, LoggedIn_ID)
		info("Sucsess", "You are now a premium user. Pleae login again to confirm")
		execute_sql(database_file, sql_update)
		cursor.execute(sql_update)
		cursor.close ()
		conn.commit()
		Purchase.hide()

def Social():
	# show the user there progress and save it in a graphic format
	Leader.show()
	advice1.hide(); advice2.hide(); advice3.hide()
	advice4.hide(); advice5.hide(); advice6.hide()
	height_txt.hide(); weight_txt.hide(); Calculate.hide()
	#this makes sure every this is hidden in case they came from another tab
	blank1.hide(); Height.hide(); Weight.hide()
	Next.hide(); Back.hide(); Learn_more.hide()
	Fadvice2.hide(); Fadvice3.hide()
	Back_workout.hide(); Chest.hide(); Biceps.hide()
	Legs_work.hide(); Cardio.hide(); Text_blank.hide()
	Logo_menu.hide(); Fadvice4.hide()
	global LoggedIn_ID
	conn= sqlite3.connect(database_file)
	c=conn.cursor()
	SQLselect = "SELECT Weight, Dateofweight from Extra_Deatails where UserID = '"+str(LoggedIn_ID)+"'"#find the nesscary data for the graph
	c.execute(SQLselect)
	df=pd.DataFrame(c.fetchall(), columns = ["Weight", "Date"])# puts them in to a usable dataframe
	print(df)
	plt.xlabel("Date")
	plt.ylabel("Weight")
	plt.bar(df["Date"], df["Weight"])# plots them as a bar
	plt.savefig("UserGraph.JPG")# save the graph as a JGP
	plt.show()
	
def Every_one():
	#this allow user to compair there progress with others
	conn= sqlite3.connect(database_file)
	c=conn.cursor()
	SQLselect_every = "SELECT Weight, Dateofweight from Extra_Deatails"
	c.execute(SQLselect_every)
	df=pd.DataFrame(c.fetchall(), columns = ["Weight", "Date"])
	print(df)
	plt.bar(df["Date"], df["Weight"], width=0.5)
	plt.savefig("Comparation Graph.JPG")
	plt.show()


def Credit():
	#check if they are going to enter card deatials
	if Card.value == 1:
		Card_deatails.enable()
		CVV.enable()
	else:
		Card_deatails.disable()
		CVV.disable()
#####################################################################################
def Calculation():
	#does the cacualtion and output for the BMI calcualtor
	if Weight == "":
		info("Error", "weight can't be blank")
	elif Height == "":
		info("Error", "height can't be blank")
	else:
		weight = float(Weight.value)
		height = float(Height.value)
		BMI = weight / (height/100)**2#does the math to caculate
		if BMI < 18.5:
			#outputs for the BMI of user
			info('BMI','Underweight')
		if BMI>=18.5 and BMI<25:
			info('BMI',"Normal")
		if BMI >= 25 and BMI < 30:
			info('BMI','Overweight')
		if BMI >= 30 and BMI < 35:
			info('BMI','Obesity Class 1')
		if BMI >= 35 and BMI < 40:
			info('BMI','Obesity Class 2')
		if BMI >= 40:
			info('BMI','Obesity Class 3')
#################################################################################
def login_user():
	#this is where we make sure when the user login they are in the database
	global LoggedIn_ID ## variable needed to know who logged in ##
	if login_input.value == "":#check if textbox is blank
		info("Username Incorect", "you must enter a valid Username")
	#elif login_input.value.isalpha() == False:# check the username is they have ented any special characters
		#info("Login Incorrect", "No special character in Username")
	elif Pass.value == "":#check if textbox is blank
		info("Password Error", "You must enter a valid Password")
	else: 
		username = login_input.value #check the database for the username
		sqlselect = "SELECT * FROM UserTbl WHERE Username = '"+username+"'"
		rows = query_database(database_file, sqlselect)
		if len(rows) == 0: ### This checks that the user was found ###
			info("Accont Error","Account not Found Please Check Username and Password")
		else:
			# check pw
			pw = hashlib.sha512(Pass.value.encode('utf8')).hexdigest()
			DBP = rows[0][2]
			if DBP  == pw:
				#show info if password is found moving you onto booking
				info("Log in","You have successfully logged in")
				LoggedIn_ID = rows [0][0]
				Cards = rows[0][8]
				if Cards == 9999999999999999:#check if the user is valid
					main()# opens non premium window
					Loginas.value = login_input.value
				else:
					Custom_Workout.enable()
					Social.enable()
					BMI_cal.enable()
					Buy_prem.hide()
					Purchase_Prem.hide()
					Loginas.value = login_input.value
					main()# opens the premium window
			else:
				info("Accont Error","Account not Found Please Check Username and Password")
#################################################################################
def check_date(Mydate): # found on geeks for geeks
# initializing format
	format = "%d/%m/%Y"
	# checking if format matches the date
	res = True
	# using try-except to check for truth value
	try:
		res = bool(datetime.strptime(Mydate, format))
	except ValueError:
		res = False
	return res
##################################
def signup_user(): 
	validdetails = False #assume there is an error
	if Card.value == 1:
	   # Paid = 1
		if Card_deatails.value == '':
			info('Error!','Please enter an input into the textbox')
		elif Card_deatails.value.isnumeric() == False:
			info('Error!','Please make sure there are only digits in the Creditcard textbox')
		elif len(Card_deatails.value) != 16:
			info('Error!','Please enter the correct length of digits in the CreditCard textbox') # All details valid for a subscription
		elif CVV.value == '':
			info('Error!','CVV can not be empty')
		elif CVV.value.isnumeric() == False:
			info('Error!','Please make sure there are only digits in the Creditcard textbox')
		elif len(CVV.value) != 3:
			info('Error!','Please enter the correct amount of digits of 3')
		else:
			validdetails = True
	if Card.value == 0:
		Paid = 0
		Card_deatails.value = '9999999999999999' # All details valid for free account
		CVV.value = "999"
	#this is where we validate the sign in window to make sure the user has entered the value for each box
		isValidDate = check_date(DateofB.value)#this is where the date gets validated and make sure its in the correct format
		if (isValidDate):
			if Uname.value == "":
				info("Error", "You must enter a valid username")
			elif len(Uname.value) < 3 or len(Uname.value) > 12 :
				info("Error", "Please enter a Username between 3 and 12 charaters")
			elif len(Pword.value) < 5 or len(Pword.value) > 20:
				info("Error", "Your Password must be between 5 and 20 characters")
			elif Fname.value == "":
				info("Error", "You must enter a First name")
			elif Sname.value == "":
				info("Error", "You must enter a Surname")
			elif len(Num.value) < 11 and Num.value.isnumeric() == False:
				info("Error", "You must enter a Valid phone number")
			elif "@" not in Email.value:
				info("Error", "You must enter a Email address")
			else:
				validdetails = True # All details valid for free account
				Cookie.show()
		if validdetails == True:
			Pw = Pword.value
			passwo = hashlib.sha512(Pw.encode('utf8')).hexdigest()
			InsertDataSQL = ("INSERT INTO UserTbl(Username, Password, Fname, Sname, Phonenumber, Email, DofB ,Card_details, CVV) VALUES ('"+ str(Uname.value) + "', '" + str(passwo) + "', '" + str(Fname.value) + "', '" +str(Sname.value)+ "', '" +str(Num.value)+ "', '" +str(Email.value)+ "' , '" +str(DateofB.value)+ "' , '"  +str(Card_deatails.value)+ "' , '" +str(CVV.value)+"')")
			#inserts the data into the data base
			execute_sql(database_file, InsertDataSQL)
			info("Success","You are now registered as:" + Fname.value)
			login.show()
			Cookie.hide()
			signup.hide()
		else:
			info('error','Invalid Details. Check Date is DD/MM/YYYY')

################################################################################
############################################################
#################################
# build main window             #
#################################
#this creates all the window for later uses
app = App(title="Toka Fitness")
login = Window(app, title="Toka Finess login", width=450, height=400, layout = "grid")
signup = Window(app, title="Toka Finess Sign Up",height=550, width=455, layout="grid")
PW_change = Window(login, title="Toka Fitness Password Reset", height=200, width=200)
Main_App = Window(app, title="Toka fitness Main menu", height=700, width=1200)
Leg = Window(app, title ="Toka Fitness Leg workouts")
chest = Window(app, title ="Toka Fitness Chest workouts")
Cookie = Window(app, title="Toka Fitness Cookies")
Purchase = Window(app, title="Toka Fitness Purchase page", height=250, width=250)
#######################################################################
#this hides them so the user only see the window they chose
login.hide()
signup.hide()
PW_change.hide()
Main_App.hide()
Leg.hide()
Cookie.hide()
chest.hide()
Purchase.hide()
#####################################################################
#this builds the main window where the user can choose to login or sign up
Acsessibiltys_box = Box(app, align="top", width = 'fill')# create a box for slide only
Size = Slider(Acsessibiltys_box, align = "left", command = Zoom_Percent ,start = 8, end=20)# create a slide for the user to zoom in
Zoom_confirm = PushButton(Acsessibiltys_box, text="confirm", command = Size_confirm, width = 4, align = "left")# allow the user to comfirm size
#
Size.hide()
Zoom_confirm.hide()
############
text_blank = Text(app, text="")
text_blank = Text(app, text="Welcome to Toka Fitness app")
text_blank = Text(app, text="")
#
user_textbox = PushButton(app, text="Login", command=Login, width=15)#goes to login
Text_blank = Text(app, text="")
##
signup1 = PushButton(app, text="Sign Up", command=Signup, width=15)# goes to signup
#
Exit = PushButton(app, text="Exit", align="bottom", command=Exit, width=15)# exits the app
#
Acsessibiltys=MenuBar(app,toplevel=["Colour", "Zoom", "Font"], options=[[["Dark Mode",Dark_Mode], ["Light Mode",Light_Mode]],# acsessibilty for the user
													  [["Zoom", Zoom]], 
													  [["courier", courier], ["Times New Roman", Roman], ["verdana", verdana], ["comic sans", comic]]])
#
#############################################
#			Login window					#
#############################################
#create the login window for the users
Logo = Picture(login, image="Toka fitness Logo.PNG", grid=[0,0], width=445, height=160, align="right")
Login_signup = PushButton(login, text="Signup", grid=[0,1],  command=Signup)
Signup_login = PushButton(login, text="login", grid=[0,1], align="left")
Signup_login.disable()

text = Text(login, text= "Enter Username:", grid=[0,2], align="left")
login_input = TextBox(login, grid=[0,2])
#
text = Text(login, text= "Enter Password:", grid=[0,3], align="left")
Pass = TextBox(login, hide_text=True,  grid=[0,3])
#
Login_btn = PushButton(login, text="Login", command = login_user, grid=[0,4])
PW_reset = PushButton(login, text="Forgot Password", command=Pass_reset, grid=[0,5])
Back_button = PushButton(login, text="Back" ,command=Back, grid=[0,11])
######################################
#			Change Password			 #
######################################
#create a window for the user to chage password
text = Text(PW_change, text= "Username")
Change_Uname = TextBox(PW_change)

text = Text(PW_change, text= "Enter Password")
New_PW = TextBox(PW_change, hide_text=True)

Change = PushButton(PW_change, text="Change Password", command=Change_PW)
Back_button = PushButton(PW_change, text="Cancel",command=Cancel)

############################
#		Cookies			   #
############################
#create a cookies window
Biscuts = Text(Cookie, text="THIS APP USES COOKIES AND OTHER SIMILAR TECHNOLOGIES")
UK_biscuts = Text(Cookie, text="This is to improve your experience and show you personalised content.\n If you are happy with the cookies and other similar technologies\n we use, hit Accept All. Alternatively, select Manage Preferences\n to either decline cookies and other similar technologies\n or manage them individually.", size=10)

UK_Biscots = Box(Cookie, layout='grid')

More_cookie = PushButton(UK_Biscots, text="Manage", command=Manage_cookies, grid=[0,0])
hide_cookie = PushButton(UK_Biscots, text='hide Details', command=hide_cookies, grid=[0,0])


AM_Biscuts = Box(Cookie, layout = "grid")

Ness = Text(AM_Biscuts, text='Strictly necessary:  ', grid=[0,0], size=10)
Ness_content = Text(AM_Biscuts, text="Strictly necessary cookies help make a app navigable\n by activating basic functions such as page navigation\n and access to secure app areas. Without these cookies,\n the app would not be able to work properly.", grid=[1,0], size=10)

Functional = Text(AM_Biscuts, text='Functional:  ', grid=[0,1], size=10)
Functional_cont = CheckBox(AM_Biscuts, text="Functional cookies make it possible to save \ninformation that changes the way the app appears or\n acts. For instance your preferred language or region", grid=[1,1])

Statistical = Text(AM_Biscuts, text='Statistical:  ', grid=[0,2], size=10)
Statistical_cont = CheckBox(AM_Biscuts, text='Statistical cookies help the app owner \nunderstand how visitors interact with the app by \ncollecting and reporting information.', grid=[1,2])

Marketing = Text(AM_Biscuts, text='Marketing:  ', grid=[0,3], size=10)
Marketing_cont = CheckBox(AM_Biscuts, text='Marketing cookies are used to track visitors\n across app. The intention is to display ads that \nare relevant and interesting to the individual user and thus \nmore valuable for publishers and third-party advertisers.', grid=[1,3])

Accept = PushButton(UK_Biscots, text='Accept Cookies', command=signup_user, grid=[1,0])

Accept_Chosen= PushButton(UK_Biscots, text='Accept Chosen Cookie', command=signup_user, grid=[1,0])

#############################################
#			signup window					#
#############################################
Logo = Picture(signup, image="Toka fitness Logo.PNG", grid=[1,0], width=450, height=160, align="right")

Login_signup = PushButton(signup, text="Signup", grid=[1,1])
Signup_login = PushButton(signup, text="login", grid=[1,1], command=Login, align="left")
Login_signup.disable()

text = Text(signup, text= "Enter a User name:", grid=[1,2], align="left")
Uname = TextBox(signup, grid=[1,2])
#
text = Text(signup, text= "Enter a Password:", grid=[1,3], align="left")
Pword = TextBox(signup, hide_text=True, grid=[1,3])
##
text = Text(signup, text= "Enter a First Name:", grid=[1,4], align="left")
Fname = TextBox(signup, grid=[1,4])
##
text = Text(signup, text= "Enter a Surname:", grid=[1,5], align="left")
Sname = TextBox(signup, grid=[1,5], )
##
text = Text(signup, text= "Enter Phone number:", grid=[1,6], align="left")
Num = TextBox(signup, grid=[1,6])
##
text = Text(signup, text= "Enter Email:", grid=[1,7], align="left")
Email = TextBox(signup,grid=[1,7])
###
##
text= Text(signup, text="Date of Birth:", grid=[1,8], align="left")
DateofB = TextBox(signup, grid=[1,8])

text = Text(signup, text= "Card Details:", grid=[1,9], align="left")
Card_deatails =TextBox(signup, enabled = False, grid=[1,9])

text = Text(signup, text="CVV:", grid=[1,10], align="left")
CVV = TextBox(signup,enabled = False, grid=[1,10])

Card = CheckBox(signup, text="Premium acsess", command=Credit, grid=[1,12],  align="left")
Terms = CheckBox(signup, text="Agree Terms and Conditions", command = do_this , grid=[1,12])


signup_button = PushButton(signup, text="Sign up", command=Cookies, grid=[1,13], enabled = False) # button on app, main window

Back_button = PushButton(signup, text="Back" ,command=Back, grid=[1,14])
#############################################
#			MAIN window						#
#############################################
Option = Box(Main_App, align="top" ,layout="grid")
#
LoginText = Text(Option, text="You are login as:", grid=[0,0], align="right")
Loginas = Text(Option, align ="left", grid=[1,0])

Food = PushButton(Option, text="Food recipes", width=15, grid=[0,1], command=Food_recipes)
#
Workout = PushButton(Option, text="Workout Advice", width=15, grid=[1,1], command=Workout_advice)

Custom_Workout = PushButton(Option, text="Custom Workouts", width=15, grid=[2,1], enabled = False, command=Custom)
Custom_Workout.when_mouse_enters = PREM

Social = PushButton(Option, text="Social", width=15, grid=[3,1], enabled = False, command = Social)
Social.when_mouse_enters = PREM

Leader = PushButton(Option, text="Show others", width=15, grid=[3,7], command=Every_one)
Leader.hide()

BMI_cal = PushButton(Option, text="BMI caculator", width=15, grid=[4,1], enabled = False, command=BMI_calc)
BMI_cal.when_mouse_enters = PREM

Purchase_Prem = PushButton(Option, text="Purchase Premium accsess", command=Buy, grid=[5,1])

Logo_menu = Picture(Main_App, image="Toka fitness Logo.PNG", width=700, height=300)

Buy_prem = Text(Main_App, text="Buy premium to access better and more enganing features", size=30)
#
Media = PushButton(Option, text="App", grid=[6,1], command = Social_media)

#
Back = PushButton(Option, text="Return to login" ,command=Login, grid=[9,1])
#############################################
#			BMI cacluator					#
#############################################
height_txt = Text(Main_App, text="Enter your height in cm: ")
Height = TextBox(Main_App, text="")

blank1 = Text(Main_App, text="")

weight_txt = Text(Main_App, text="Enter your weight in kg: ")
Weight = TextBox(Main_App, text=" ")

Calculate = PushButton(Main_App, text="Calculate", width=15, command=Calculation)

#############################################
#			Custom workouts					#
#############################################
Legs_work = PushButton(Main_App, text="Legs workouts", command = Leg_workouts)
Text_blank = Text(Main_App)

Back_workout = PushButton(Main_App, text="Back workouts", command = Under_construction)
Text_blank = Text(Main_App)

Chest = PushButton(Main_App, text="Chest workouts", command = chest_workouts)
Text_blank = Text(Main_App)

Cardio = PushButton(Main_App, text="Cardio workouts",  command = Under_construction)
Text_blank = Text(Main_App)

Biceps = PushButton(Main_App, text="Biseps and Triceps workouts",  command = Under_construction)

#############################################
#			Workout advice						#
#############################################
advice1 = Picture(Main_App, image="Workout adivce 1.JPG", visible = False, width = 600, height = 300)
advice2 = Picture(Main_App, image="Workout adivce 2.JPG", visible = False, width = 600, height = 300)
advice3 = Picture(Main_App, image="Workout adivce 3.JPG", visible = False, width = 600, height = 300)
advice4 = Picture(Main_App, image="Workout adivce 4.JPG", visible = False, width = 600, height = 300)
advice5 = Picture(Main_App, image="Workout adivce 5.JPG", visible = False, width = 600, height = 300)
advice6 = Picture(Main_App, image="Workout adivce 6.JPG", visible = False, width = 600, height = 300)
Back_Next = Box(Main_App, layout = "grid")

Back = PushButton(Back_Next, text="Back", width=15, command=Back_image, grid=[0,0])

Next = PushButton(Back_Next, text="Next", width=15, command=Next_image, grid=[1,0])

Learn_more = PushButton(Back_Next, text="Learn more", grid=[2,0])

Learn_more.when_clicked = WorkoutLearnMore
#############################################
#			Food advice						#
#############################################
Fadvice1 = Picture(Main_App, image="Food adivce 1.JPG", visible = False, width = 600, height = 300)
Fadvice2 = Picture(Main_App, image="Food adivce 2.JPG", visible = False, width = 600, height = 300)
Fadvice3 = Picture(Main_App, image="Food adivce 3.JPG", visible = False, width = 600, height = 300)
Fadvice4 = Picture(Main_App, image="Food adivce 4.JPG", visible = False, width = 600, height = 300)

Back_Next = Box(Main_App, layout = "grid")

F_Next = PushButton(Back_Next, text="Next", width=10 ,command=FNext, grid=[1,0])

F_Back = PushButton(Back_Next, text="Back", width=10, command=FBack, grid=[0,0])

More_recipes = PushButton(Back_Next, text="Learn more", grid=[2,0])
More_recipes.when_clicked = Learn_More_recipes

#####################################
#			Legs				#####
#####################################
#creates the leg exasice window
Next_Back = Box(Leg, align="bottom")
#
Exercises1 = Text(Leg, text="Exercises 1: Barbell Squats")
Squats = Picture(Leg, image="high-bar.GIF", width = 400, height = 300)
Exercises1_reps = Text(Leg, text="Do three set of 6 Reps Going up in weight")

Exercises2 = Text(Leg, text="Exercises2: Deadlift")
Deadlift = Picture(Leg, image="deadlift.GIF", width = 400, height = 300, visible = False)
Exercises2_reps = Text(Leg, text="Do three set of 4 Reps Going up in weight")

Exercises3 = Text(Leg, text="Exercises3: Bulgarian Split Squats")
Bulgarian = Picture(Leg, image="Bulgarian-Split-Squat.GIF", width = 400, height = 300, visible = False)
Exercises3_reps = Text(Leg, text="Go till Failier")

Leg_Next = PushButton(Next_Back, align="right", text="Next", command=Next_Exercises)
Leg_Back = PushButton(Next_Back, align="right", text="Back", command=Back_Exercises)
######
Exercises2_reps.hide()
Exercises2.hide()
Exercises3.hide()
Exercises3_reps.hide()
Leg_Back.hide()

#####################################
#				Chest			#####
#####################################
#this create the chest workout window with 
Next_Back = Box(chest, align="bottom")

Exercises1 = Text(chest, text="Exercises 1: Barbell Bench Press")
Bench = Picture(chest, image="Barbell-Bench-Press.gif", width = 400, height = 300)
Exercises1_reps = Text(chest, text="Do three set of 6 Reps Going up in weight")

Exercises2 = Text(chest, text="Exercises 2: Chest Press")
Chress_Press = Picture(chest, image="chest-press.gif", width = 400, height = 300, visible = False)
Exercises2_reps = Text(chest, text="Do three set of 4 Reps Going up in weight")

Exercises3 = Text(chest, text="Exercises 3: Cable-Crossover")
Cable = Picture(chest, image="Cable-Crossover.gif", width = 400, height = 300, visible = False)
Exercises3_reps = Text(chest, text="Do Till failier")

Next_chest = PushButton(Next_Back, align="right", text="Next", command=Chest_Next)
Back_Chest = PushButton(Next_Back, align="right", text="Back", command=Chest_Back)

Exercises2_reps.hide()
Exercises2.hide()
######
Exercises3_reps.hide()
Exercises3.hide()
Back_Chest.hide()

############################
#### purtchase premium #####
############################
#create the purchase window for the user to enter there details
text_blank = Text(Purchase, text="")

text= Text(Purchase, text="Please enter Card Numbers")
Num_Card= TextBox(Purchase)

text_blank = Text(Purchase, text="")

text= Text(Purchase, text="Please enter CVV")
CVV_Num= TextBox(Purchase)

text_blank = Text(Purchase, text="")

Confirm = PushButton(Purchase, text="Confirm Payment", command=confirm)

app.display()
