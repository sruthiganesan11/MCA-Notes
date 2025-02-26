## Doubly Linked List

```
#include<iostream.h>
#include<conio.h>
#include<malloc.h>

struct node {
    int info;
    node *next, *back;
};

class list {
    node *root, *end;
public:
    list() { root = end = NULL; }
    void createinfo();
    void insert();
    void delet();
    void display();
};

void list::createinfo() {
    node *p = NULL, *n;
    int t;
    cout << "Enter -999 to stop: ";
    cin >> t;
    while (t != -999) {
	n = (node*)malloc(sizeof(node));
	n->info = t;
	n->next = NULL;
	n->back = p;
	if (!root) root = n;
	else p->next = n;
	p = n;
	cout << "Enter -999 to stop: ";
	cin >> t;
    }
    end = p;
}

void list::display() {
    node *x = root;
    cout << "parent->";
    while (x) {
	cout << x->info << "->";
	x = x->next;
    }
    cout << "parent\n";
}

void list::insert() {
    node *temp = (node*)malloc(sizeof(node)), *ex = root;
    int value, pos, i = 1;
    cout << "Enter the value & position to insert: ";
    cin >> value >> pos;
    temp->info = value;
    temp->next = temp->back = NULL;

    if (pos == 1) {
	temp->next = root;
	if (root) root->back = temp;
	root = temp;
    } else {
	while (ex && i < pos - 1) { ex = ex->next; i++; }
	if (ex) {
	    temp->next = ex->next;
	    temp->back = ex;
	    if (ex->next) ex->next->back = temp;
	    ex->next = temp;
	    if (!temp->next) end = temp;
	}
    }
}

void list::delet() {
    node *ex = root;
    int p, i = 1;
    cout << "Enter the position to delete: ";
    cin >> p;

    if (p == 1 && root) {
	root = root->next;
	if (root) root->back = NULL;
    } else {
	while (ex && i < p - 1) { ex = ex->next; i++; }
	if (ex && ex->next) {
	    node *temp = ex->next;
	    ex->next = temp->next;
	    if (temp->next) temp->next->back = ex;
	    else end = ex;
	    free(temp);
	}
    }
}

void main() {
    clrscr();
    list one;
    one.createinfo();
    one.display();
    one.insert();
    one.display();
    one.delet();
    one.display();
    getch();
}

```
