import mysql.connector as c
connect=c.connect(host='localhost',
              user='root',
              password='1234',
              database='hospital')
cursor=connect.cursor()
if connect.is_connected():
    print("Welcome To ABC Bank")


while True:
    condition=input("Please press 1 for OPEN ACCOUNT \n Please press 2 for CASH DEPOSIT \n Please press 3 for CASH WITHDRAWL \n Please press 4 for ACCOUNT DETAILS \n Please press 5 for EXIT\n")
    #OpenAccount
    if condition=="1":
        name=input("Please enter your full name ")
        query="select count('{}') from user where name='{}'".format(name, name)
        cursor.execute(query)
        name_count=cursor.fetchone()
        name_count = str(name_count).replace("(", "")
        name_count = name_count.replace(")", "")
        name_count = name_count.replace(",", "")
        if(float(name_count)>0):
            print("Name already exists")
            break;
        age=int(input("Please enter your age "))
        address=input("Please enter your address ")
        mobile=int(input("Please enter your mobile number "))
        amount=int(input("Please enter the amount to open bank account "))
        query="insert into user values('{}',{},'{}',{},{})".format(name,age,address,mobile,amount)
        cursor.execute(query)
        connect.commit()
        print("Account open Sucessfully")
    #CashDeposit
    elif condition=="2":
        name=input("Please enter your full name ")
        amount=int(input("Enter the amount you want to deposit "))
        query = "select amount from user where name='{}'".format(name)
        cursor.execute(query)
        old_amount = cursor.fetchone()
        old_amount = str(old_amount).replace("(", "")
        old_amount = old_amount.replace(")", "")
        old_amount = old_amount.replace(",", "")
        amount = amount + float(old_amount)
        query = "update user set amount={} where name='{}'".format(amount,name)
        cursor.execute(query)
        connect.commit()
        print("Total amount in your BankAccount ",amount)
    #CashWithdrawl
    elif condition=="3":
        name = input("Please enter your full name ")
        amount = int(input("Enter the amount you want to withdraw "))
        query="select amount from user where name='{}'".format(name)
        cursor.execute(query)
        old_amount = cursor.fetchone()
        old_amount = str(old_amount).replace("(", "")
        old_amount = old_amount.replace(")", "")
        old_amount = old_amount.replace(",", "")
        if (float(old_amount) < amount):
            print("Insuffcient balance for this transaction\nPlease check your balance")
        else:
            amount = float(old_amount) - amount
            print(amount)
            query = "update user set amount={} where name='{}'".format(amount, name)
            cursor.execute(query)
            connect.commit()
            print("Your current balance is",old_amount)
    #AccountDetails
    elif condition=="4":
        name = input("Please enter your full name ")
        query="select * from user where name='{}'".format(name)
        cursor.execute(query)
        account_info=cursor.fetchone()
        print(account_info)
        connect.commit()
    #Exit
    elif condition=="5":
        print("Exit")
        break;
