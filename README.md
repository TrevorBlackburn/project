A = 0
print("Hello! welcome to the banking system")
print("if you could please put in your account number and PIN number please!")
print("")

User_Account_Number = 12345678910
User_PIN_Number = 4321
while A == 0:
    Account_Number = int(input("Account Number?: "))
    print("")
    if Account_Number == User_Account_Number:
        print("Alright! I found your account!")
        A = A + 1
    else:
        print("Uh oh, I dont see a account linked to that number try again?")
print("")

while A == 1:
    PIN_Number = int(input("PIN number?: "))
    print("")
    if PIN_Number == User_PIN_Number:
        print("Alright! That PIN works!")
        A = A + 1
    else:
        print("Uh oh, this PIN dosent work for this account, try again?")
print("")

print("welcome to your account! what would you like to do?")
print("")
print("[withdraw]")
print("--------")
print("[deposit]")
print("--------")
print("[check balence]")
