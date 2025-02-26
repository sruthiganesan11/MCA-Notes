## Evaluation of Expression

```
#include <iostream.h>
#include <conio.h>
#include <string.h>
#include <ctype.h>

#define MAX 30

class Stack
{
    int top, s[MAX];

public:
    Stack() { top = -1; }
    void push(int x) { s[++top] = x; }
    int pop() { return s[top--]; }
};

int evaluate(char exp[], int isPrefix)
{
    Stack st;
    int l = strlen(exp);
    int i = isPrefix ? l - 1 : 0, step = isPrefix ? -1 : 1;

    while (i >= 0 && i < l)
    {
        if (isdigit(exp[i]))
            st.push(exp[i] - '0');
        else
        {
            int b = st.pop(), a = st.pop();
            if (isPrefix)
            { // Manual swap for Prefix evaluation
                int temp = a;
                a = b;
                b = temp;
            }
            switch (exp[i])
            {
            case '+':
                st.push(a + b);
                break;
            case '-':
                st.push(a - b);
                break;
            case '*':
                st.push(a * b);
                break;
            case '/':
                st.push(a / b);
                break;
            }
        }
        i += step;
    }
    return st.pop();
}

void main()
{
    clrscr();
    char exp[MAX];
    int choice;

    while (1)
    {
        cout << "\nEvaluation of Expression.\n";
        cout << "1: Prefix\n2: Postfix\n3: Exit\n";
        cin >> choice;
        if (choice == 3)
            break;

        cout << "ENTER THE " << (choice == 1 ? "PREFIX" : "POSTFIX") << " EXPRESSION: ";
        cin >> exp;
        cout << "Result: " << evaluate(exp, choice == 1) << "\n";
    }
    cout << "End";
    getch();
}

```
