## Student Marklist

```
#include <iostream.h>
#include <conio.h> // For clrscr() and getch()
#define MAX 100 // Maximum number of students


struct Student {
    char name[50];  // Using char array instead of string
    int rollNo;
    int marks[3];
    int total;
    float average;
};

int main() {
    int n;
    Student students[MAX]; // Using a fixed-size array

    clrscr(); // Clears the screen for Turbo C++
   
    cout << "Enter number of students: ";
    cin >> n;

    // Input student details
    for (int i = 0; i < n; i++) {
        cout << "\nEnter Name: ";
        cin >> students[i].name; // Avoids getline() issues

        cout << "Enter Roll No: ";
        cin >> students[i].rollNo;

        students[i].total = 0;
        for (int j = 0; j < 3; j++) {
            cout << "Enter Mark " << (j + 1) << ": ";
            cin >> students[i].marks[j];
            students[i].total += students[i].marks[j];
        }
        students[i].average = students[i].total / 3.0;
    }

    // Output student details
    cout << "\nNAME\tROLL NO\tMARK1\tMARK2\tMARK3\tTOTAL\tAVERAGE\n";
    for (int i = 0; i < n; i++) {
        cout << students[i].name << "\t" << students[i].rollNo;
        for (int j = 0; j < 3; j++)
            cout << "\t" << students[i].marks[j];
        cout << "\t" << students[i].total << "\t" << students[i].average << "\n";
    }

    getch(); // Waits for key press before closing (Turbo C++)
    return 0;
}
```