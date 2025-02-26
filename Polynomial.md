## Polynomial

```
#include <iostream.h>
#include <conio.h>

class Polynomial {
    int power, *coeffs;
public:
    Polynomial(int deg = 3) {
        power = deg;
        coeffs = new int[deg + 1];
    }
    void GetCoeffs() {
        for (int i = power; i >= 0; i--) cin >> coeffs[i];
    }
    void Show() {
        for (int i = power; i >= 0; i--) {
            if (i != power) cout << " + ";
            cout << coeffs[i];
            if (i > 1) cout << "x^" << i;
            else if (i == 1) cout << "x";
        }
        cout << endl;
    }
    Polynomial operator+(Polynomial &X) {
        Polynomial Z(power);
        for (int i = power; i >= 0; i--) Z.coeffs[i] = coeffs[i] + X.coeffs[i];
        return Z;
    }
    Polynomial operator-(Polynomial &X) {
        Polynomial Z(power);
        for (int i = power; i >= 0; i--) Z.coeffs[i] = coeffs[i] - X.coeffs[i];
        return Z;
    }
};

void main() {
    int ch;
    clrscr();
    do {
        cout << "\n========================";
        cout << "\n1.addition of Polynomial\n2.subtraction of Polynomial\n3.Exit";
        cout << "\n========================\nEnter your choice: ";
        cin >> ch;
        if (ch == 1 || ch == 2) {
            Polynomial X, Y, Z;
            cout << "Enter the value for first Poly\n";
            X.GetCoeffs();
            cout << "Enter the value for Second Poly\n";
            Y.GetCoeffs();
            cout << "\nshow the First Polynomial\n";
            X.Show();
            cout << "\nshow the second Polynomial\n";
            Y.Show();
            Z = (ch == 1) ? X + Y : X - Y;
            cout << "\n" << ((ch == 1) ? "Show the Add Polynomial " : "view the Subtraction of two Polynomial ");
            Z.Show();
        }
    } while (ch != 3);
}

```
