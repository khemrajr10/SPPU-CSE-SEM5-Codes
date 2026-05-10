class Bankacc:
	def __init__(self):
		self.balance=0

	def deposit(self):
		amt=int(input("Amount to be deposited:"))
		self.balance+=amt
		print("Amout deposited",amt)

	def withdraw(self):
		amt=int(input("Amount to be withdraw:"))
		if(self.balance>=amt):
			self.balance-=amt
			print("Amout withdraw",amt)
		else:
			print("Insufficient fund")
	
	def display(self):
		print("Net Balance:",self.balance)

s=Bankacc()
while(True):		
	choice=int(input("Enter which operation you want to perform:\n1.Deposite \n2.Withdraw"))
	
	if(choice==1):	
		s.deposit()
		s.display()
	elif(choice==2):
		s.withdraw()
		s.display()
	else:
		break
