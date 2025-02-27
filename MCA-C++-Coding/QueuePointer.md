## Queue Pointer

```
#include <iostream.h>
#include <conio.h>
#include <ctype.h>

struct Node {
    int data;
    Node* next;
    Node(int val) { data = val; next = NULL; }
};

class Queue {
    Node *front, *rear;
public:
    Queue() { front = rear = NULL; }

    void enqueue(int val) {
        Node* newNode = new Node(val);
        if (!rear) front = rear = newNode;
        else rear->next = newNode, rear = newNode;
        display();
    }

    void dequeue() {
        if (!front) cout << "Queue is empty\n";
        else {
            Node* temp = front;
            front = front->next;
            if (!front) rear = NULL;
            delete temp;
            display();
        }
    }

    void display() {
        if (!front) cout << "Queue is empty\n";
        else {
            cout << "first==>";
            for (Node* temp = front; temp; temp = temp->next)
                cout << temp->data << "==>";
            cout << "last\n";
        }
    }
};

void main() {
    Queue q;
    char choice;
    int value;

    clrscr();
    do {
        cout << "\nInsert (I) | Delete (D) | View (V) | Exit (E)\nEnter choice: ";
        cin >> choice;
        switch (toupper(choice)) {
            case 'I': cout << "Enter value: "; cin >> value; q.enqueue(value); break;
            case 'D': q.dequeue(); break;
            case 'V': q.display(); break;
            case 'E': cout << "Exiting...\n"; break;
            default: cout << "Invalid choice!\n";
        }
    } while (toupper(choice) != 'E');
    
    getch();
    return 0;
}
```
