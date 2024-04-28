# Testing
//This program computes the median of a set of numbers.
#include <iostream>

using namespace std;

void selectSort(int *A, int n);
void swap(int &a, int &b);
void print(int *A, int d);
double median (int *A, int n);

int main(){
    int * A;
    int m;
    cout << "How many items are you working with? (< 1 to quit): ";
    cin >> m;
    while (m > 0){
        A = new int [m];
        for (int i = 0; i < m; i++){
        cout << "Element " << i+1 << " is: ";
        cin >> A[i];
        }
        print (A, m);
        cout << endl;
        selectSort(A, m);
        print(A, m);
        cout << endl;
        cout << "The median is: " << median(A, m) << endl;
        delete [] A;
        A = nullptr;
        cout << "How many items are you working with? (< 1 to quit): ";
        cin >> m;
    }


    





    return 0;
}

void swap(int& a, int &b){
    int temp = a;
    a = b;
    b = temp;
}

void selectSort(int *A, int n){
    int index, position, smallest;
    for (index = 0; index < n-1; index++){
        smallest = index;
        for (position = index + 1; position < n; position++)
        if (A[position] < A[smallest])
        smallest = position;
        swap (A[smallest], A[index]);
    }
}



void print(int *A, int d){
    int i;
    for (i = 0; i < d; i++){
        cout << A[i];
        if (i < d-1)
        cout << ", ";
    }
    
}

double median (int *A, int n){
    selectSort (A, n);
    if (n%2 != 0)
    return A[n/2];
    return (A[n/2 - 1] + A[n/2])/ 2.0;
}