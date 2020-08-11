# s_linklist
#include<stdio.h>
#include<stdlib.h>
#include<malloc.h>
typedef struct node{
	int data;
	struct node *next;
}nod;
nod * head =NULL;
void insert_first(){
  nod * new1;  
    int item;  
    new1 = (nod *) malloc(sizeof(nod));  
    if(new1 == NULL)  
    {  
        printf("\nOVERFLOW");  
    }  
    else  
    {  
        printf("\nEnter value\n");    
        scanf("%d",&item);    
        new1->data = item;  
        new1->next = head;  
        head = new1;  
        printf("\nNode inserted");  
    }  
	}
void insert_last(){
	nod *new1;
	new1=(nod *)malloc(sizeof(nod));
	printf("Enter a new number\n");
	scanf("%d",&new1->data);
		if(head==NULL){
			new1->next=head;
			head=new1;
			printf("Node Inserted Successfully\n");
		}else{
			nod *temp=head;
			while(temp->next!=NULL){
				temp=temp->next;
			}
			temp->next=new1;
			new1->next=NULL;
			printf("Node Inserted Successfully\n");
			
		}
}
void insert_ith_position(int value,int pos){
	int i=0;
	nod * new1;
	new1=(nod *)malloc(sizeof(nod));
	new1->data=value;
	if(head==NULL){
		new1->next=NULL;
		head=new1;
	}else{
		nod * temp=head;
		for(i=0;i<pos-1;i++){
			temp=temp->next;
		}
		new1->next=temp->next;
		temp->next=new1;
	}
	printf("Node inserted successfully\n");

}
void traverse(){
	int count=0;
	if(head==NULL){
		printf("Link List is empty\n");
	}else{
	nod * temp= head;
	printf("Link List is:\n");
	while(temp!=NULL){
		if(temp->next == NULL){
			printf("%d\n",temp->data);
		}else{
			printf("%d-->",temp->data);
		}
	temp=temp->next;
	count++;
		
	}
	printf("Link list has %d nodes\n",count);
	}
	
}
void delete_first(){

	   int t=head->data;
	   if(head==NULL){
	   	printf("Link list is empty\n");
	   }else{
	   	while(head!=NULL){
		head=head->next;
		printf("%d node is deleted\n",t);
		break;
		}
	   }
	
}
void delete_last(){
	nod * temp=head;
	if(head->next==NULL){
		head=NULL;
		}else{
			while(head!=NULL){
				if(head->next->next==NULL){
					head->next=NULL;
				}
				head=head->next;
			}
			head=temp;
		}
		printf("Node deleted\n");
}
void delete_ith_position(int pos){
	int i,flag=0;
	nod * temp1=head , *temp2;
	if(pos==1){
		head=temp1->next;
		free(temp1);
		printf("Node is deleted\n");
	}else{
		for(i=0;i<pos-1;i++){
			if(temp1->next != NULL){
				temp2=temp1;
				temp1=temp1->next;
			}else{
				flag=1;
				break;
			}
		}
		if(flag==0){
			temp2->next=temp1->next;
			free(temp1);
			printf("Node deleted\n");
		}
	}
	
}
void search(){
	int f=0,n;
	nod * temp =head;
	printf("Enter the node number to be searched\n");
	scanf("%d",&n);
	while(temp!=NULL){
		if(n==temp->data)
		{
			f=1;
		}
		temp=temp->next;
	}
	if(f==0){
		printf("%d is not present in the Link List\n",n);
	}else{
		printf("%d is present in the Link List\n",n);
	}
}
void sort(){
	int temp;
	nod * i,*j;
	for(i=head;i->next!=NULL; i=i->next){
		for(j=i->next;j!=NULL; j=j->next){
			if(i->data>j->data){
				temp=i->data;
				i->data=j->data;
				j->data=temp;
			}
		}
	}
	printf("The Shorted list is:\n");
	traverse();
}
int main(){
	int c,value,pos,p;
	while(1){
		printf("\n--------------------------------------------------------------------------\n");
		printf("\t\t\t-----SINGLY LINKLIST MENU-----\n");
		printf("\n1.INSERT-FIRST|2.DISPLAY|3.EXIT|4.INSERT-LAST|5.DELETE-FIRST\n6.DELETE-LAST|7.SEARCH|8.SORT|9.INSERT-iTH-POSITION|10.DELETE-iTH-POSITION\n");
		printf("-----------------------------------------------------------------------------\n");
		printf("\nEnter your choice\n");
		scanf("%d",&c);
		switch(c){
			case 1: insert_first();break;
			case 2: traverse();break;
			case 3: exit(1);
			case 4: insert_last();break;
			case 5: delete_first();break;
			case 6: delete_last();break;
			case 7: search();break;
			case 8: sort();break;
			case 9:
				    printf("Enter the value to be inserted\n");
				    scanf("%d",&value);
				    printf("Enter the position after which you want to inserted\n");
				    scanf("%d",&pos);
					insert_ith_position(value,pos);break;
			case 10:
					printf("Enter the position to be deleted\n");
					scanf("%d",&p);
					delete_ith_position(p);break;		
			default: printf("Wrong choice????\n");
		}
	}
	return 0;
}
