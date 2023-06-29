import pandas as pd
import datetime
import matplotlib.pyplot as plt
import hashlib

def login():
    count = 3
    for i in range(3):
        username = input("Please enter your username..:")
        password = input("Please enter your password..:")
        password = hashlib.sha512(password.encode('utf8')).hexdigest()
        for line in open("Uname&Pword.txt","r").readlines():
            login_info = line.split()
            if username == login_info[0] and password == login_info[1]:
                print("Correct credentials!")
                return True
            print("Incorrect credentials.")
            count -= 1
            print("you have",count, "goes left")
    else:
        print("you have no goes left")
        return False
#
#
#
#
def profit_loss_menu():
    flag = True
    while flag:
        print("###############################################")
        print("Welcome! Please choose an option from the list")
        print("1. Show profit/loss for specific products")
        print("2. Show profit/loss for all products")
        print("3. quantity of Product sold from suppliers")
        print("4. Show profit/loss from suppliers")
        print("###############################################")

        profit_loss_choice = input("Please enter the number of your choice (1-4): ")

	      # This code tries to convert the input into an int
	      # if it fails, the except: path is executed, otherwise the else path
        try:  
            int(profit_loss_choice)
        except:
            print("Sorry, you did not enter a valid choice")
            flag = True
        else:
            if int(profit_loss_choice) < 1 or int(profit_loss_choice) > 4:
                print("Sorry, you did not enter a valid choice")
                flag = True
            else:
                return int(profit_loss_choice) 
#
#
#
#
#
def get_product_choice():
    flag = True
    while flag:
        print("######################################################")
        print("Please choose a product from the list:")
        print("Please enter the number of the product (1-16)")
        print("1.  Potatoes")
        print("2.  Carrots")
        print("3.  Peas")
        print("4.  Lettuce")
        print("5.  Onions")
        print("6.  Apples")
        print("7.  Oranges")
        print("8.  Pears")
        print("9.  Lemons")
        print("10. Limes")
        print("11. Melons")
        print("12. Cabbages")
        print("13. Asparagus")
        print("14. Broccoli")
        print("15. Cauliflower")
        print("16. Celery")
        print("######################################################")

        product_list = ["Potatoes", "Carrots", "Peas", "Lettuce", "Onions", 
"Apples", "Oranges", "Pears", "Lemons", "Limes","Melons", "Cabbages", 
"Asparagus", "Broccoli", "Cauliflower", "Celery"]

        product_choice = input("Please enter the number of your choice (1-16): ")
	      # This checks the input is an integer
        try:
            int(product_choice)
        except:
            print("Sorry, you did not enter a valid choice")
            flag = True
        else:
            if int(product_choice) < 1 or int(product_choice) > 16:
                print("Sorry, you did not enter a valid choice")
                flag = True
            else:
                product_name = product_list[int(product_choice)-1]
                return product_name
#
#
#
#
#
#
def get_start_date():
    flag = True
    while flag:
        start_date = input('Please enter start date for your time range (DD/MM/YYYY) ')
        # This checks the start date is a valid date
        try:
           pd.to_datetime(start_date)
        except:
            print("Sorry, you did not enter a valid date")
            flag = True
        else:
            start_date_return = pd.to_datetime(start_date, dayfirst=True)
            if (pd.isnull(start_date_return) == True):
                print("Sorry, you did not enter a valid date")
                flag = True
            else:
                return start_date_return
#
#
#
#
#
def get_end_date():
    flag = True
    while flag:
        end_date = input('Please enter end date for your time range (DD/MM/YYYY) ')
        # This checks the end date is a valid date
        try:
           pd.to_datetime(end_date)
        except:
            print("Sorry, you did not enter a valid date")
            flag = True
        else:
            end_date_return = pd.to_datetime(end_date, dayfirst=True)
            if (pd.isnull(end_date_return) == True):
                print("Sorry, you did not enter a valid date")
                flag = True
            else:
                return end_date_return
#
#
#
#

def get_date_range_all():
    # df1 is a pandas data frame being created from a csv file
    df1 = pd.read_csv("Task4a_data.csv") 

    df1["Date"] = pd.to_datetime(df1["Date"], dayfirst=True) # convert Date column to be a datetime object

    # This selects all the rows between the dates and removes the Supplier column completely
    # results is another data frame
    results = df1.loc[(df1["Date"] >= start_date) & (df1["Date"] <= end_date), df1.columns != "Supplier"].copy()
    
    # Calculate some new columns from existing columns
    results["Cost Subtotal"] = results["KGs Purchased"] * results["Purchase Price"]
    results["Sales subtotal"] = results["KGs Sold"] * results["Selling Price"]
    results["Profit subtotal"] = results["Sales subtotal"] - results["Cost Subtotal"]
    
    total = round(results["Profit subtotal"].sum(),2)
    
    # The to_string function just makes the Pandas data frame look nice
    # without the index (index = False)
    results_print = results.to_string(index=False)
    print(results_print)

    # The format function is just a convenient way to make a string to print out
    # Anything between the {} is replaced with the value of the variables that are passed to the string
    print("The overall profit/loss for the selected time frame was £{}".format(total))
#
#
#
#
#
def get_date_range_product():
    product_name = get_product_choice()
    # df2 is a pandas data frame from the complete csv file
    df2 = pd.read_csv("Task4a_data.csv") 

    df2["Date"] = pd.to_datetime(df2["Date"], dayfirst=True) # convert Date column to be a datetime object

    # This selects all the rows in the data frame between the dates and for the chosen product 
    # and makes a new data frame called product_results
    product_results = df2.loc[(df2["Date"] >= start_date) & (df2["Date"] <= end_date) & (df2["Product"] == product_name)].copy()

    # Calculate some new columns from existing columns
    product_results["Cost Subtotal"] = product_results["KGs Purchased"] * product_results["Purchase Price"]
    product_results["Sales subtotal"] = product_results["KGs Sold"] * product_results["Selling Price"]
    product_results["Profit subtotal"] = product_results["Sales subtotal"] - product_results["Cost Subtotal"]
    
    total = round(product_results["Profit subtotal"].sum(),2)
    # The to_string function just makes the Pandas data frame look nice
    results_print = product_results.to_string(index=False)
    
    print(results_print)
    # The format function is just a convenient way to make a string to print out 
    # Anything between the {} is replaced with the value of the variables that are passed to the string
    print("The profit/loss for the {} for the selected time frame was £{}".format(product_name, total))
    #
    #
    #
    #

def get_Supplier_choice():
    #this is the function that lets the user chose what company they would like to see
    flag = True
    while flag:
        print("""
        Please choose a product from the list:
        Please enter the number of the product (1-5)
        ######################################################
        1.  Clean Living
        2.  Farm Direct
        3.  Grocers Int.
        4.  Natural Best
        5.  Natural Food
        ######################################################""")
        #this is the list of suppliers that the user can see this is display once they pick the option to eaith see profit and loss or quantity sold
        Suppliers_list = ["Clean Living", "Farm Direct", "Grocers Int.", "Natural Best", "Natural Food"]

        Suppliers_choice = input("Please enter the number of your choice (1-5): ")
        #this is where they input the choses they would like to choose from 1-5
        try:
            int(Suppliers_choice)
            #this test to see of the chose os a integer
        except:
            print("Sorry, you did not enter a valid choice")
            #if it is not valid the it will display this message and will loop
            flag = True
        else:
            if int(Suppliers_choice) < 1 or int(Suppliers_choice) > 5:
                print("Sorry, you did not enter a valid choice")
                flag = True
                #this check weather the input is between 1 and 5 if not it loops and displays an error message
            else:
                Supplier_name = Suppliers_list[int(Suppliers_choice)-1]
                return Supplier_name
#
#
#
#
#
def get_Supplier():
    #this def statment is where the quntity of the product from the supplier is shown
    Supplier_name =  get_Supplier_choice()#this pull the table up to choose the supplierr
    df3 = pd.read_csv("Task4a_data.csv") #this read the csv file

    df3["Date"] = pd.to_datetime(df3["Date"], dayfirst=True)#this finds all the relevent product between the 2 dates
    #
    Suppliers_results = df3.loc[(df3["Date"] >= start_date) & (df3["Date"] <= end_date) & (df3["Supplier"] == Supplier_name)].copy()#this take the suppliers name and finds the info linked to it
    #
    Suppliers_results.sort_values(by = 'Date', inplace = True)# this sorts the data by date so it is in order
    results_print = Suppliers_results.to_string(index=False)# this change the index / table to a string getting it ready for printing
    
    print(results_print)# prints the table/index
    plt.title(f'quantity of product sold from {Supplier_name}')# this is the name of graph
    plt.xlabel('Dates')# x axis lable
    plt.ylabel('KGs Purchased')# y axis lable
    plt.bar(Suppliers_results['Product'], Suppliers_results['KGs Sold'])# this tells the graph what to display
    plt.xticks(rotation=45)# make the x axis look nice
    plt.show()# shows the table
#
#
#
#
#
def Profit_suppliers():
    #this is the profit and loss segment of the code where it shows the product and loss.
    Supplier_name =  get_Supplier_choice()#this pull the table up to choose the supplier
    df4 = pd.read_csv("Task4a_data.csv") #this read the csv file

    df4["Date"] = pd.to_datetime(df4["Date"], dayfirst=True)# this gets the date that the user entered

    Suppliers_results = df4.loc[(df4["Date"] >= start_date) & (df4["Date"] <= end_date) & (df4["Supplier"] == Supplier_name)].copy()#this gets the suppliers name that the 
    #
    Suppliers_results["Cost Subtotal"] = Suppliers_results["KGs Purchased"] * Suppliers_results["Purchase Price"]#this caculates the cost subtotal
    Suppliers_results["Sales subtotal"] = Suppliers_results["KGs Sold"] * Suppliers_results["Selling Price"]# this caculate the sale subtotal
    Suppliers_results["Profit subtotal"] = Suppliers_results["Sales subtotal"] - Suppliers_results["Cost Subtotal"]#this caculates the profit subtotal
    #
    total = round(Suppliers_results["KGs Purchased"].sum(),2)
    del Suppliers_results["Purchase Price"]
    del Suppliers_results["Selling Price"]
    del Suppliers_results["Cost Subtotal"]
    del Suppliers_results["Sales subtotal"]
    del Suppliers_results["KGs Purchased"]
    del Suppliers_results["KGs Sold"]
    del Suppliers_results["Date"]
    del Suppliers_results["Supplier"]
    Suppliers_results = Suppliers_results.groupby(['Product']).sum().reset_index()
    results_print = Suppliers_results.to_string(index=False)
    #Suppliers_results.sort_values(by = 'Date', inplace = True)
    #total = round(Suppliers_results["KGs Purchased"].sum(),2)
    results_print = Suppliers_results.to_string(index=False)
    
    print(results_print)
    plt.title(f'Profit/Loss from {Supplier_name}')
    plt.xlabel('Data')
    plt.ylabel('Profit subtotal')
    plt.bar(Suppliers_results['Product'], Suppliers_results['Profit subtotal'])
    plt.xticks(rotation=45)
    plt.show()
    print(results_print)
    print("The profit/loss for the {} for the selected time frame was £{}".format(Supplier_name, total))
    #
    #
def process_menu_choice():
    if profit_choice == 1:
        get_date_range_product()
        quit()
    if profit_choice == 2:
        get_date_range_all()
        quit()
    if profit_choice == 3:
        get_Supplier()
        quit()
    if profit_choice == 4:
        Profit_suppliers()
        #quit()
    else:
        get_date_range_all()
#
#
#
authorised = login()
if authorised == True:
    start_date = get_start_date()
    end_date = get_end_date()
    profit_choice = profit_loss_menu()
    pres = process_menu_choice()
