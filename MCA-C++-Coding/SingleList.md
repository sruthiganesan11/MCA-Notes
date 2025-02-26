## Singly Linked list

```
#include <iostream.h>
#include <conio.h>
#include <stdlib.h>

struct Node
{
    int data;
    Node *next;
};

class SList
{
    Node *head;

public:
    SList() { head = NULL; }
    void insert(int);
    void display();
    void del();
};

void SList::insert(int val)
{
    Node *newNode = (Node *)malloc(sizeof(Node));
    newNode->data = val;
    newNode->next = head;
    head = newNode;
}

void SList::display()
{
    if (!head)
    {
        cout << "\nList is empty!";
        return;
    }
    Node *temp = head;
    cout << "\nList: ";
    while (temp)
    {
        cout << temp->data << " -> ";
        temp = temp->next;
    }
    cout << "NULL";
}

void SList::del()
{
    if (!head)
    {
        cout << "\nUnderflow!";
        return;
    }
    Node *temp = head;
    cout << "\nDeleted: " << temp->data;
    head = head->next;
    free(temp);
}

void main()
{
    clrscr();
    SList list;
    char choice;
    int val;

    do
    {
        cout << "\n[C]reate  [I]nsert  [D]isplay  [E]rase  [X]Exit\n";
        cout << "Choice: ";
        choice = getch();
        cout << choice << endl;

        switch (choice)
        {
        case 'C':
        case 'I':
            cout << "Enter value: ";
            cin >> val;
            list.insert(val);
            break;
        case 'D':
            list.display();
            break;
        case 'E':
            list.del();
            break;
        case 'X':
            exit(0);
        }
    } while (choice != 'X');

    getch();
}

```