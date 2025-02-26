## Student Marklist

```
#include <iostream.h>
#include <conio.h> // For clrscr() and getch()
#define MAX 100 // Maximum number of students
#define MAX_SUBJECTS 5 // Maximum subjects allowed


struct Student {
    char name[50];  
    int rollNo;
    int marks[MAX_SUBJECTS]; 
    int total;
    float average;
};

int main() {
    int studentCount, subjectCount;
    Student students[MAX]; 

    clrscr(); 
    
    cout << "Enter number of students: ";
    cin >> studentCount;
    
    // Ensure valid subject input
    do {
        cout << "Enter number of subjects (Max 5): ";
        cin >> subjectCount;
        if (subjectCount > MAX_SUBJECTS || subjectCount <= 0) {
            cout << "Invalid! Please enter a number between 1 and " << MAX_SUBJECTS << ".\n";
        }
    } while (subjectCount > MAX_SUBJECTS || subjectCount <= 0);

    // Input student details
    for (int a = 0; a < studentCount; a++) {
        cout << "\nEnter Name: ";
        cin >> students[a].name; 

        cout << "Enter Roll No: ";
        cin >> students[a].rollNo;

        students[a].total = 0;
        for (int b = 0; b < subjectCount; b++) {
            cout << "Enter Mark " << (b + 1) << ": ";
            cin >> students[a].marks[b];
            students[a].total += students[a].marks[b];
        }
        students[a].average = (float)students[a].total / subjectCount;
    }

    // Output student details
    cout << "\nNAME\tROLL NO";
    for (int c = 0; c < subjectCount; c++) cout << "\tMARK" << (c + 1);
    cout << "\tTOTAL\tAVERAGE\n";

    for (int d = 0; d < studentCount; d++) {
        cout << students[d].name << "\t" << students[d].rollNo;
        for (int e = 0; e < subjectCount; e++) 
            cout << "\t" << students[d].marks[e];
        cout << "\t" << students[d].total << "\t" << students[d].average << "\n";
    }

    getch(); 
    return 0;
}

```