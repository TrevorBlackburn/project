class BankAccount:
    def __init__(self, account_number, pin, name, balance):
        self.account_number = account_number
        self.pin = pin
        self.name = name
        self.balance = balance
    
    def check_balance(self):
        return self.balance
    
    def deposit(self, amount):
        self.balance += amount
    
    def withdraw(self, amount):
        if self.balance >= amount:
            self.balance -= amount
        else:
            print("Insufficient balance.")
    
    def modify(self, name=None, pin=None):
        if name:
            self.name = name
        if pin:
            self.pin = pin
    
    def close_account(self):
        # code to close account goes here
        pass

class Bank:
    def __init__(self):
        self.accounts = {}
    
    def create_account(self, account_number, pin, name, balance=0):
        if account_number in self.accounts:
            print("Account number already exists.")
        else:
            account = BankAccount(account_number, pin, name, balance)
            self.accounts[account_number] = account
    
    def get_account(self, account_number, pin):
        account = self.accounts.get(account_number)
        if account and account.pin == pin:
            return account
        else:
            print("Invalid account number or PIN.")
            return None
    
    def modify_account(self, account_number, pin, name=None, new_pin=None):
        account = self.get_account(account_number, pin)
        if account:
            account.modify(name, new_pin)
    
    def close_account(self, account_number, pin):
        account = self.get_account(account_number, pin)
        if account:
            account.close_account()
            del self.accounts[account_number]

# Example usage:
bank = Bank()

# Create a new account
bank.create_account("1234", "4321", "Alice", 1000)

# Get an existing account and check balance
account = bank.get_account("1234", "4321")
if account:
    print("Account balance:", account.check_balance())

# Deposit money
account.deposit(500)
print("New balance:", account.check_balance())

# Withdraw money
account.withdraw(200)
print("New balance:", account.check_balance())

# Modify account name and PIN
bank.modify_account("1234", "4321", name="Alice Smith", new_pin="1234")

# Close account
bank.close_account("1234", "1234")
