# phython.banking
class Account:
    def __init__ (self,id,holder_name):
        self.id=id
        self.holder_name=holder_name
        self._balance=0

    def check_balance(self):
        print(f"Balance={self.balance}")

    def deposit(self,amount):
        self._balance+=amount
        print("Amount deposited successfully")

    def withdraw(self,amount):
        if self._balance>=amount:
            self._balance-=amount
            print(f"updated_balance={self._balance}")
        else:
            print("Unable to withdraw")

class SavingsAccount(Account):
        def calculate_interest(self):
            Interest_rate=0.04
            interest =self._balance*Interest_rate
            print(f"interest={interest}")
class CurrentAccount(Account):
    def withdarw(self,amount):
        Overdraft_limit=10000
        if self._balance+Overdraft_limit>=amount:
                self._balance-=amount
                print(f"updated_balance={self._balance}")
        else:
            print("Exceeding the limit")
        
class bank():
    def __init__ (self,name,city):
        self.name=name
        self.city=city
        self._Account={}

    def create_Account(self,id,holder_name,type):
        if type=="Savings":
            new_account = SavingsAccount(id,holder_name)
        elif type=="current":
            new_account = CurrentAccount(id,holder_name)
        self._Account[id]=new_account
        print("Account created successfullyyyy!!!")
        return new_account
        

ibk=bank("Inchara bank of karnataka","bangalore")

s1=ibk.create_Account("6","inchara","Savings")
c1=ibk.create_Account("2","keerthi","current")

s1.deposit(1000)
c1.deposit(10)

s1.withdraw(2000)
c1.withdraw(200)

s1.calculate_interest()
