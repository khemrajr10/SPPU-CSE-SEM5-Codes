#include<iostream>
#include<string.h>
using namespace std;
 struct node
{    int prn;
      char name[50];
      node *next;
};
class sll
{        node *s=NULL,*head1=NULL,*temp1=NULL,*head2=NULL,*temp2=NULL,*head=NULL,*temp=NULL;
        int b,i,j,ct,prn1;
        char a[20];
        public:
    
            node *create();
            void insertp();
            void insertm();
	    void inserte();
            void delm();
            void delp();
            void dels();
            void display();
            void count();
            void concat();
            
}  ;        
node *sll::create()
{   node *p=new(struct node);
     cout<<"enter name of student ";
     cin>>a;
     strcpy(p->name,a);
     cout<<"\n  enter prn no. of student \n";
     cin>>b;
     p->prn=b;
     p->next=NULL;
     return  p;
  } 
  void sll::inserte()
  { 
       node *p=create();
   
     if(head==NULL)
     {    head=p;
     }
    else
    {      temp=head;
          while(temp->next!=NULL)
          {    temp=temp->next;   }
              temp->next=p;
     }        
         
   }


void sll::insertm()
  { 
       node *p=create();
   	cout<<"Enter after which prn u want to insert";
	cin>>prn1;
     if(head==NULL)
     {    head=p;
     }
    else
    {      temp=head;
          while(temp->prn!=prn1)
          {    temp=temp->next;   }
	p->next=temp->next;              
	temp->next=p;
	      	
     }        
         
   }
     void sll::insertp()
  { 
       node *p=create();
   
     if(head==NULL)
     {    head=p;
     }
    else
    {      temp=head;
            head=p;
              head->next=temp->next;
             
     }        
         
   }
  
   void sll::display()
   {          if(head==NULL)
               {    cout<<"linklist is empty";
                }
              else
              {   
                temp=head;
                          cout<<"     prn        NAME   \n";
                          while(temp!=NULL)
                          {     cout<<" \n\t"<<temp->prn<<"  \t "<<temp->name;
                                temp=temp->next;
                          }
                         //cout<<"    "<<temp->prn<<"    "<<temp->name;
               }     
  }
  void sll::delm()
  {  int m,f=0; 
     cout<<"\n enter the prn no. of student whose data you want to delete";
      cin>>m;
      temp=head;
      while(temp->next!=NULL)
      {  
           if(temp->prn==m)
            {           s->next=temp->next;
                         delete(temp);        f=1;
            }
            s=temp;
            temp=temp->next;
       }      if(f==0)
             {   cout<<"\n sorry memeber not deleted ";   }
   }
   void sll::delp()
  {     temp=head;
      head=head->next;
         delete(temp);
      }
      void sll::dels()
  {   
      temp=head;
      while(temp->next!=NULL)
      {   s=temp;
      temp=temp->next;
      }     s->next=NULL;
         delete(temp);
               
   }
   void sll::count()
   {      temp=head;    ct=0;
          while(temp!=NULL)
          {    temp=temp->next; ct++;   }
             
             cout<<"  Count of members is:"<<ct;
             
     }
     
     void sll::concat()
    {  int k,j;
       cout<<"enter no. of members in list1";
       cin>>k;
        head=NULL;
       for(i=0;i<k;i++)
       { insertm();
         head1=head;
          
       } head=NULL;
      cout<<"enter no. of members in list2";
       cin>>j;
       for(i=0;i<j;i++)
       { insertm();
         head2=head;
        
       } head=NULL;
            
        temp1=head1;
      while(temp1->next!=NULL)
	{   
	temp1=temp1->next;   
	}
        temp1->next=head2;
                       
        temp2=head1;                
        cout<<"     prn        NAME   \n";
      while(temp2->next!=NULL)
         { 
      	cout<<"\n    "<<temp2->prn<<"    "<<temp2->name<<"\n";
          temp2=temp2->next;
         }
         cout<<"\n    "<<temp2->prn<<"    "<<temp2->name<<"\n";
     }   
  int main()
  { sll s;
  int i;
   
          char ch;
       do{
          cout<<"\n choice the options";
          cout<<"\n  1. To insert president   ";
          cout<<"\n  2. To insert member   ";
          cout<<"\n  3. To insert secretary ";
          cout<<"\n  4. To delete president   ";
          cout<<"\n  5. To delete member  ";
          cout<<"\n  6. To delete secretary ";
          cout<<"\n  7. To display data   ";
          cout<<"\n  8. Count of members";
          cout<<"\n  9.To concatenate two strings ";
          cin>>i;
         switch(i)
         {        case 1:   s.insertp();
                                  break;
                  case 2:   s.insertm();
                                  break;
                  case 3:   s.inserte();
                                  break;
                  case 4:   s.delp();
                                  break;
                  case 5:   s.delm();
                                  break;
                  case 6:   s.dels();
                                  break;
                  case 7:   s.display();   
                                  break;
                  case 8:   s.count();
                                  break;      
                      
                  case 9:  s.concat();
                                                      
                                  break;                                  
                  default:  cout<<"\n unknown choice";
          }
            cout<<"\n do you want to continue enter y/Y \n";
            cin>>ch;
       
       }while(ch=='y'||ch=='Y');                                                                                                   
                     
   return 0;
 }  
