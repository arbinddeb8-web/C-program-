1.
#include <iostream>
using namespace std;

int main()
{
    int n, rev = 0, rem, temp;

    cout << "Enter a number: ";
    cin >> n;

    temp = n;

    while (n > 0)
    {
        rem = n % 10;
        rev = rev * 10 + rem;
        n = n / 10;
    }

    if (temp == rev)
        cout << "Number is Palindrome";
    else
        cout << "Number is Not Palindrome";

    return 0;
}

#include <iostream>
#include <string>
using namespace std;

int main()
{
    string str, rev = "";

    cout << "Enter a string: ";
    cin >> str;

    for (int i = str.length() - 1; i >= 0; i--)
    {
        rev = rev + str[i];
    }

    if (str == rev)
        cout << "String is Palindrome";
    else
        cout << "String is Not Palindrome";

    return 0;
}
2. 
#include <iostream>
using namespace std;

// Call by Value
void callByValue(int x)
{
    x = x + 10;
    cout << "Inside Call by Value: " << x << endl;
}

// Call by Reference
void callByReference(int &y)
{
    y = y + 10;
    cout << "Inside Call by Reference: " << y << endl;
}

int main()
{
    int a = 20, b = 20;

    cout << "Before Call by Value: " << a << endl;
    callByValue(a);
    cout << "After Call by Value: " << a << endl;

    cout << "\nBefore Call by Reference: " << b << endl;
    callByReference(b);
    cout << "After Call by Reference: " << b << endl;

    return 0;
}
3.#include <iostream>
using namespace std;

// Function to add two matrices
void addMatrices(int rows, int cols, int matrix1[][10], int matrix2[][10], int result[][10]) {
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            result[i][j] = matrix1[i][j] + matrix2[i][j];
        }
    }
}

// Function to subtract two matrices
void subtractMatrices(int rows, int cols, int matrix1[][10], int matrix2[][10], int result[][10]) {
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            result[i][j] = matrix1[i][j] - matrix2[i][j];
        }
    }
}

// Function to multiply two matrices
void multiplyMatrices(int rows1, int cols1, int matrix1[][10], int rows2, int cols2, int matrix2[][10], int result[][10]) {
    for (int i = 0; i < rows1; i++) {
        for (int j = 0; j < cols2; j++) {
            result[i][j] = 0; // Initialize result matrix
            for (int k = 0; k < cols1; k++) {
                result[i][j] += matrix1[i][k] * matrix2[k][j];
            }
        }
    }
}

// Function to transpose a matrix
void transposeMatrix(int rows, int cols, int matrix[][10], int result[][10]) {
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            result[j][i] = matrix[i][j];
        }
    }
}

// Function to display a matrix
void displayMatrix(int rows, int cols, int matrix[][10]) {
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            cout << matrix[i][j] << " ";
        }
        cout << endl;
    }
}

int main() {
    int matrix1[10][10], matrix2[10][10], result[10][10];
    int rows1, cols1, rows2, cols2;
    int choice;

    // Input for first matrix
    cout << "Enter the number of rows and columns for Matrix 1: ";
    cin >> rows1 >> cols1;
    cout << "Enter the elements of Matrix 1:\n";
    for (int i = 0; i < rows1; i++) {
        for (int j = 0; j < cols1; j++) {
            cin >> matrix1[i][j];
        }
    }

    // Input for second matrix
    cout << "Enter the number of rows and columns for Matrix 2: ";
    cin >> rows2 >> cols2;
    cout << "Enter the elements of Matrix 2:\n";
    for (int i = 0; i < rows2; i++) {
        for (int j = 0; j < cols2; j++) {
            cin >> matrix2[i][j];
        }
    }

    // Menu-driven switch case
    cout << "\nSelect operation to perform: \n";
    cout << "1. Add Matrices\n2. Subtract Matrices\n3. Multiply Matrices\n4. Transpose Matrix 1\n5. Transpose Matrix 2\n";
    cout << "Enter your choice: ";
    cin >> choice;

    switch (choice) {
        case 1:
            if (rows1 == rows2 && cols1 == cols2) {
                addMatrices(rows1, cols1, matrix1, matrix2, result);
                cout << "\nResult of Addition:\n";
                displayMatrix(rows1, cols1, result);
            } else {
                cout << "Addition not possible. Matrices must have the same dimensions.\n";
            }
            break;

        case 2:
            if (rows1 == rows2 && cols1 == cols2) {
                subtractMatrices(rows1, cols1, matrix1, matrix2, result);
                cout << "\nResult of Subtraction:\n";
                displayMatrix(rows1, cols1, result);
            } else {
                cout << "Subtraction not possible. Matrices must have the same dimensions.\n";
            }
            break;

        case 3:
            if (cols1 == rows2) {
                multiplyMatrices(rows1, cols1, matrix1, rows2, cols2, matrix2, result);
                cout << "\nResult of Multiplication:\n";
                displayMatrix(rows1, cols2, result);
            } else {
                cout << "Multiplication not possible. Number of columns in Matrix 1 must equal number of rows in Matrix 2.\n";
            }
            break;

        case 4:
            transposeMatrix(rows1, cols1, matrix1, result);
            cout << "\nTranspose of Matrix 1:\n";
            displayMatrix(cols1, rows1, result);
            break;

        case 5:
            transposeMatrix(rows2, cols2, matrix2, result);
            cout << "\nTranspose of Matrix 2:\n";
            displayMatrix(cols2, rows2, result);
            break;

        default:
            cout << "Invalid choice!\n";
    }

    return 0;
}
4.#include <iostream>
#include <cmath>

using namespace std;

class Shape {
private:
    double radius;
    double length;
    double width;

public:
    // Constructor for circle (using radius)
    Shape(double r) : radius(r), length(0), width(0) {
        cout << "Circle created with radius: " << radius << endl;
    }

    // Constructor for rectangle (using length and width)
    Shape(double l, double w) : length(l), width(w), radius(0) {
        cout << "Rectangle created with length: " << length << " and width: " << width << endl;
    }

    // Destructor
    ~Shape() {
        cout << "Shape object destroyed." << endl;
    }

    // Method to calculate the perimeter of a circle
    double calculateCirclePerimeter() const {
        if (radius > 0) {
            return 2 * M_PI * radius;
        } else {
            cout << "Invalid radius for circle." << endl;
            return 0;
        }
    }

    // Method to calculate the perimeter of a rectangle
    double calculateRectanglePerimeter() const {
        if (length > 0 && width > 0) {
            return 2 * (length + width);
        } else {
            cout << "Invalid length or width for rectangle." << endl;
            return 0;
        }
    }
};

int main() {
    // Creating a circle object with radius 5
    Shape circle(5);
    cout << "Perimeter of the circle: " << circle.calculateCirclePerimeter() << endl;

    // Creating a rectangle object with length 4 and width 6
    Shape rectangle(4, 6);
    cout << "Perimeter of the rectangle: " << rectangle.calculateRectanglePerimeter() << endl;

    return 0;
}
7.#include <iostream>
#include <cmath>
using namespace std;

// Function overloading: same function name "AREA", different parameter lists

// 1 argument -> Circle (radius)
float AREA(float radius) {
    return 3.14159f * radius * radius;
}

// 2 arguments -> Rectangle (length, breadth)
float AREA(float length, float breadth) {
    return length * breadth;
}

// 3 arguments -> Triangle (using Heron's formula, sides a, b, c)
float AREA(float a, float b, float c) {
    float s = (a + b + c) / 2.0f;   // semi-perimeter
    return sqrt(s * (s - a) * (s - b) * (s - c));
}

int main() {
    float radius, length, breadth, a, b, c;

    cout << "Enter radius of circle: ";
    cin >> radius;
    cout << "Area of Circle = " << AREA(radius) << endl;

    cout << "\nEnter length and breadth of rectangle: ";
    cin >> length >> breadth;
    cout << "Area of Rectangle = " << AREA(length, breadth) << endl;

    cout << "\nEnter three sides of triangle: ";
    cin >> a >> b >> c;
    cout << "Area of Triangle = " << AREA(a, b, c) << endl;

    return 0;
}
8.#include <iostream>
#include <iomanip>
#include <cstring>
using namespace std;

// ---------------- Base class ----------------
class Student {
protected:
    int  rollNo;
    char name[64];

public:
    void getStudentData() {
        cout << "Enter Roll No   : ";
        cin  >> rollNo;
        cout << "Enter Name      : ";
        cin.ignore();
        cin.getline(name, 64);
    }

    void showStudentData() {
        cout << "Roll No : " << rollNo << "\n";
        cout << "Name    : " << name   << "\n";
    }
};

// ---------------- Derived class (Level 1) ----------------
// Exam inherits Student
class Exam : public Student {
protected:
    float marks[6];   // marks in 6 subjects

public:
    void getExamData() {
        cout << "\nEnter marks in 6 subjects (out of 100 each):\n";
        for (int i = 0; i < 6; i++) {
            cout << "  Subject " << (i + 1) << " : ";
            cin  >> marks[i];
        }
    }

    void showExamData() {
        cout << "\nMarks obtained:\n";
        for (int i = 0; i < 6; i++)
            cout << "  Subject " << (i + 1) << " : " << marks[i] << "\n";
    }
};

// ---------------- Derived class (Level 2) ----------------
// Result inherits Exam, which inherits Student  -> MULTILEVEL INHERITANCE
class Result : public Exam {
private:
    float totalMarks;
    float percentage;
    char  grade;

    void calculateResult() {
        totalMarks = 0;
        for (int i = 0; i < 6; i++)
            totalMarks += marks[i];

        percentage = totalMarks / 6.0f;   // 6 subjects, out of 100 each

        if (percentage >= 90)      grade = 'A';
        else if (percentage >= 75) grade = 'B';
        else if (percentage >= 60) grade = 'C';
        else if (percentage >= 40) grade = 'D';
        else                       grade = 'F';
    }

public:
    void processResult() {
        getStudentData();   // from Student
        getExamData();      // from Exam
        calculateResult();  // own method
    }

    void displayResult() {
        cout << "\n==================================================\n";
        cout << "                   RESULT SHEET\n";
        cout << "==================================================\n";
        showStudentData();  // from Student
        showExamData();     // from Exam
        cout << fixed << setprecision(2);
        cout << "\nTotal Marks : " << totalMarks << " / 600\n";
        cout << "Percentage  : " << percentage   << " %\n";
        cout << "Grade       : " << grade        << "\n";
        cout << "==================================================\n";
    }
};

int main() {
    int n;
    cout << "Enter number of students: ";
    cin  >> n;

    Result *res = new Result[n];

    for (int i = 0; i < n; i++) {
        cout << "\n--- Student " << (i + 1) << " ---\n";
        res[i].processResult();
    }

    cout << "\n\n############ FINAL RESULTS ############\n";
    for (int i = 0; i < n; i++)
        res[i].displayResult();

    delete [] res;
    return 0;
}
9.#include <iostream>
using namespace std;

// Forward declaration needed because ClassA's friend declaration
// refers to ClassB before ClassB has been fully defined.
class ClassB;

class ClassA {
private:
    int num;   // private member - normally not accessible outside the class

public:
    ClassA(int n) : num(n) {}

    void display() const {
        cout << "ClassA number = " << num << endl;
    }

    // Declares swapNumbers() as a friend: it is NOT a member of ClassA,
    // but it is still allowed to access ClassA's private data.
    friend void swapNumbers(ClassA &a, ClassB &b);
};

class ClassB {
private:
    int num;   // private member

public:
    ClassB(int n) : num(n) {}

    void display() const {
        cout << "ClassB number = " << num << endl;
    }

    // Same function is also declared a friend of ClassB,
    // so it can access ClassB's private data too.
    friend void swapNumbers(ClassA &a, ClassB &b);
};

// Definition of the friend function.
// Because it is a friend of BOTH classes, it can directly touch
// a.num and b.num even though "num" is private in each class.
void swapNumbers(ClassA &a, ClassB &b) {
    int temp = a.num;
    a.num = b.num;
    b.num = temp;
}

int main() {
    int x, y;

    cout << "Enter first number (for ClassA object)  : ";
    cin  >> x;
    cout << "Enter second number (for ClassB object) : ";
    cin  >> y;

    ClassA objA(x);
    ClassB objB(y);

    cout << "\nBefore swapping:\n";
    objA.display();
    objB.display();

    swapNumbers(objA, objB);   // friend function call - not objA.swapNumbers(...)

    cout << "\nAfter swapping:\n";
    objA.display();
    objB.display();

    return 0;
}
10.#include <iostream>
#include <cstring>
using namespace std;

// ---------------- Base class ----------------
class Media {
protected:
    char title[64];
    char publication[64];

public:
    // Virtual functions: the version called is decided at RUN TIME
    // by the actual type of the object, not the type of the pointer.
    virtual void read() {
        cin.ignore(1000, '\n');
        cout << "Enter title       : ";
        cin.getline(title, 64);
        cout << "Enter publication : ";
        cin.getline(publication, 64);
    }

    virtual void show() {
        cout << "Title       : " << title << "\n";
        cout << "Publication : " << publication << "\n";
    }

    // Virtual destructor: ensures the derived class destructor runs
    // when an object is deleted through a base class pointer.
    virtual ~Media() {}
};

// ---------------- Derived class 1 ----------------
class Book : public Media {
    int pages;

public:
    void read() {                 // overrides Media::read()
        cout << "\n--- Enter Book details ---\n";
        Media::read();            // reuse base class input
        cout << "Enter number of pages : ";
        cin  >> pages;
    }

    void show() {                 // overrides Media::show()
        cout << "\n[BOOK]\n";
        Media::show();
        cout << "Pages       : " << pages << "\n";
    }
};

// ---------------- Derived class 2 ----------------
class Tape : public Media {
    float playTime;               // in minutes

public:
    void read() {                 // overrides Media::read()
        cout << "\n--- Enter Video Tape details ---\n";
        Media::read();
        cout << "Enter playing time (minutes) : ";
        cin  >> playTime;
    }

    void show() {                 // overrides Media::show()
        cout << "\n[VIDEO TAPE]\n";
        Media::show();
        cout << "Play time   : " << playTime << " minutes\n";
    }
};

int main() {
    const int MAX = 10;
    Media *items[MAX];            // array of BASE class pointers
    int count = 0;
    int choice;

    do {
        cout << "\n1. Add Book\n2. Add Video Tape\n3. Display all\n0. Exit\nChoice: ";
        cin  >> choice;

        if (choice == 1 && count < MAX) {
            items[count] = new Book();     // base pointer -> derived object
            items[count]->read();          // calls Book::read() (virtual)
            count++;
        }
        else if (choice == 2 && count < MAX) {
            items[count] = new Tape();     // base pointer -> derived object
            items[count]->read();          // calls Tape::read() (virtual)
            count++;
        }
        else if (choice == 3) {
            cout << "\n========== BOOK SHOP STOCK ==========";
            for (int i = 0; i < count; i++)
                items[i]->show();          // correct show() chosen at run time
            cout << "\n=====================================\n";
        }
        else if ((choice == 1 || choice == 2) && count >= MAX) {
            cout << "Shop is full!\n";
        }
    } while (choice != 0);

    for (int i = 0; i < count; i++)
        delete items[i];                   // virtual destructor -> proper cleanup

    return 0;
}
11.#include <iostream>
#include <cstring>
using namespace std;

// ---------------- Base class ----------------
class Student {
protected:
    int  rollNo;
    char name[64];

public:
    void getStudent() {
        cout << "Enter Roll No : ";
        cin  >> rollNo;
        cout << "Enter Name    : ";
        cin.ignore(1000, '\n');
        cin.getline(name, 64);
    }

    void showStudent() {
        cout << "Roll No : " << rollNo << "\n";
        cout << "Name    : " << name   << "\n";
    }
};

// ---------------- Intermediate class 1 ----------------
// "virtual" here makes Test share ONE copy of Student with other classes
class Test : virtual public Student {
protected:
    float theory[3];          // marks in 3 theory subjects

public:
    void getTestMarks() {
        cout << "Enter marks in 3 theory subjects (out of 100):\n";
        for (int i = 0; i < 3; i++) {
            cout << "  Subject " << (i + 1) << " : ";
            cin  >> theory[i];
        }
    }
};

// ---------------- Intermediate class 2 ----------------
class Sports : virtual public Student {
protected:
    float sportsMarks;        // marks in sports (out of 100)

public:
    void getSportsMarks() {
        cout << "Enter sports marks (out of 100) : ";
        cin  >> sportsMarks;
    }
};

// ---------------- Final derived class ----------------
// Inherits from BOTH Test and Sports (diamond shape).
// Without "virtual" above, Result would contain two copies of Student
// and rollNo/name would be ambiguous.
class Result : public Test, public Sports {
    float total;

public:
    void calculate() {
        total = theory[0] + theory[1] + theory[2] + sportsMarks;
    }

    void display() {
        showStudent();        // unambiguous: only one Student sub-object exists
        cout << "Theory Marks : " << theory[0] << ", "
             << theory[1] << ", " << theory[2] << "\n";
        cout << "Sports Marks : " << sportsMarks << "\n";
        cout << "TOTAL MARKS  : " << total << " / 400\n";
    }
};

int main() {
    Result r;

    r.getStudent();       // from the single shared Student
    r.getTestMarks();     // from Test
    r.getSportsMarks();   // from Sports
    r.calculate();

    cout << "\n=========== RESULT ===========\n";
    r.display();
    cout << "==============================\n";

    return 0;
}


