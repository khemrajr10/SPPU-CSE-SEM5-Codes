print("Matrix A")
row1=int(input("Enter no. of rows"))
col1=int(input("Enter no. of cols"))
A=[[0 for j in range(col1)] for i in range(row1)]


for i in range(row1):
	for j in range(col1):
		A[i][j]=int(input())

print("Matrix A:",A)

print("Matrix B")
row2=int(input("Enter no. of rows"))
col2=int(input("Enter no. of cols"))
B=[[0 for j in range(col2)] for i in range(row2)]


for i in range(row2):
	for j in range(col2):
		B[i][j]=int(input())

print("Matrix B:",B)


def add():
	if(row1==row2 and col1==col2):
		C=[[0 for j in range(col2)] for i in range(row2)]
		for i in range(row2):
			for j in range(col2):
				C[i][j]=A[i][j]+B[i][j]
		print("Result of Addition",C) 
	else:
		print("Addition not Possible")

def sub():
	if(row1==row2 and col1==col2):
		C=[[0 for j in range(col2)] for i in range(row2)]
		for i in range(row2):
			for j in range(col2):
				C[i][j]=A[i][j]-B[i][j]
		print("Result of Subtraction:",C) 
	else:
		print("Subtraction not Possible")

def Transpose():
	print("Enter matrix for Transpose:")
	row=int(input("Enter no. of rows"))
	col=int(input("Enter no. of cols"))
	T=[[0 for j in range(col)] for i in range(row)]

	for i in range(row):
		for j in range(col):
			T[i][j]=int(input())

	print(T)
	C=[[0 for j in range(col)] for i in range(row)]
	for i in range(row):
		for j in range(col):
			C[i][j]=T[j][i]
	print("Tranpose Matrix:",C) 
	
def mul():
	if(col1==row2):
		C=[[0 for j in range(col2)] for i in range(row2)]
		for i in range(row1):
			for j in range(col2):
				C[i][j]=0
				for k in range(col2):
					C[i][j]+=A[i][k]*B[k][j]
		print("Result of Multiplication:",C) 
	else:
		print("Multiplication not Possible")


while(True):		
	choice=int(input("Enter which operation you want to perform:\n1.Addition \n2.Subtraction\n3.Multiplication\n4.Transpose"))
	if(choice==1):	
		add()
		
	elif(choice==2):
		sub()

	elif(choice==3):
		mul()
	
	elif(choice==4):
		Transpose()
		
	else:
		break
