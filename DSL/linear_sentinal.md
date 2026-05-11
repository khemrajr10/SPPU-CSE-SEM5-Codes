n=int(input("Enter no. of students attended Training Program:"))
print("Enter roll no.s in Random order")
l=[]
for i in range(n):
	e=int(input())
	l.append(e)

def linear(l,n):
	key=int(input("Enter the roll no. to be search:"))

	for i in range(0,n):
		if(l[i]==key):
			return i
	return -1
			
	



def sentinel(l,n):
	
	key=int(input("Enter the roll no. to be search:"))
	last=l[n-1]
	l[n-1]=key
	
	while(l[i]!=key):
		i+=1
	l[n-1]=last
	if (i<n-1 or l[n-1]==key):
		return i
	else:	
		return -1
 
	

while(True):
	print("\n ")
	print("Linear/Sentinel search")
	print("1.Linear Search\n2.Sentinel Search")
	choice=int(input("Enter choice:"))
	if choice==1:
		a=linear(l,n)
		if(a==-1):
			print("Element not Found ")

		else:
			print("Element Found at location:",a)
	elif choice==2:
		a=sentinel(l,n)
		if(a==-1):
			print("Element not Found ")
		else:
			print("Element Found at location:",a)	
	else:
		print("Wrong Choice")
		break
