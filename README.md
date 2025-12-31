# Vivek_08_bankclass BankAccount:
    def __init__(self, account_number, name, balance=0):
        self.account_number = account_number
        self.name = name
        self.balance = balance

    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            print(f"₹{amount} deposited successfully.")
        else:
            print("Invalid deposit amount.")

    def withdraw(self, amount):
        if amount > self.balance:
            print("Insufficient balance.")
        elif amount <= 0:
            print("Invalid withdrawal amount.")
        else:
            self.balance -= amount
            print(f"₹{amount} withdrawn successfully.")

    def display_balance(self):
        print(f"Account Holder: {self.name}")
        print(f"Account Number: {self.account_number}")
        print(f"Available Balance: ₹{self.balance}")


# -------- Main Program --------
accounts = {}

while True:
    print("\n===== BANK MENU =====")
    print("1. Create Account")
    print("2. Deposit")
    print("3. Withdraw")
    print("4. Check Balance")
    print("5. Exit")

    choice = input("Enter your choice: ")

    if choice == "1":
        acc_no = input("Enter Account Number: ")
        name = input("Enter Account Holder Name: ")
        balance = float(input("Enter Initial Balance: "))
        accounts[acc_no] = BankAccount(acc_no, name, balance)
        print("Account created successfully.")

    elif choice == "2":
        acc_no = input("Enter Account Number: ")
        if acc_no in accounts:
            amount = float(input("Enter amount to deposit: "))
            accounts[acc_no].deposit(amount)
        else:
            print("Account not found.")

    elif choice == "3":
        acc_no = input("Enter Account Number: ")
        if acc_no in accounts:
            amount = float(input("Enter amount to withdraw: "))
            accounts[acc_no].withdraw(amount)
        else:
            print("Account not found.")

    elif choice == "4":
        acc_no = input("Enter Account Number: ")
        if acc_no in accounts:
            accounts[acc_no].display_balance()
        else:
            print("Account not found.")

    elif choice == "5":
        print("Thank you for using the bank system.")
        break

    else:
        print("Invalid choice. Please try again.")
