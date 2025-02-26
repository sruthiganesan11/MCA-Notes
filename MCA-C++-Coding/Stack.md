## Implementation Of stack

```
#include<iostream.h>
#include<conio.h>

#define MAX 100

class Stack {
private:
int stack[MAX];
int top;

public:
Stack() {top = -1;}

void push(int data) {
if(top == (MAX -1)) {
cout <<"Stack Overflow!" <<endl;
}
else {
stack[++top]=data;
display();
}
}

void pop() {
if(top == -1) {
cout<<"Stack is underflow!Nothing to pop." <<endl;
}
else{
top--;
display();
 }
}

void display() {
if(top == -1) {
cout <<"Stack is empty."<<endl;
}
else{
cout<<"Stack elements:";

for(int i = top; i >= 0; i--) {
cout << stack[i] << " ";
}
cout << endl;
}
}
};

int main() {
Stack s;
int data, choice;

clrscr();

do{
cout<<"\n1.Push\n2.Pop\n3.Quit"<<endl;
cout<<"Enter your choice:";
cin>>choice;

switch(choice){
case 1:
cout<<"Enter a number to push:";
cin>>data;
s.push(data);
break;

case 2:
s.pop();
break;

case 3:
cout<<"Exiting..."<<endl;
break;
default:
cout<<"Invalid choice.Try again."<<endl;
}
}
while(choice != 3);
getch();
return 0;
}

```