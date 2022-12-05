# Anita Balasanyan
## Contact Info:
Phone: +995 579 503 322
Email: balasanyananita@gmail.com

## Summary
I am 18 years old. I have some work experience. I am very ambitious and hawdworking. 


## Skills
* HTML
* C++
* Figma
* Photoshop

## Code Examples
```
#include <iostream>
#include <fstream>
#include <vector>
using namespace std;
void fillVector(vector<int> & , string);
void printVector(const vector<int> & );
int BinarySearch(const vector<int> &,int );
int main()
{
  vector<int> sorted;  
  fillVector(sorted,"sorted_numbers.txt");
  printVector(sorted);
  int check;
  cout << "\nEnter number to be checked: ";
  cin >> check;
  int index = BinarySearch(sorted, check);
  if(index == -1)
     cout << "\nVeqtor does not contain "
          << check << endl;
  else cout << "\nVeqtor contains " << check 
            << ", index is " << index << endl;        
}
void fillVector(vector <int> & a, string fileName){
   int number;  
   ifstream ifs(fileName);
   while( ifs >> number ) 
      a.push_back(number);    
}
int BinarySearch(const vector<int> & a, int c)
{
   int l = 0, r = a.size()-1, m;
    while( l <= r ){
       m = (l + r)/2;
       if(c == a[m]) return m;
       if(c > a[m]) l = m + 1;
       else r = m - 1;     
   }
    return -1;      
}
void printVector(const vector<int> & x)
{
   cout << "Vector is: \n\n";  
   for(size_t i{}; i < x.size(); i++)
       cout << x[i] << ' ';
   cout << endl;     
}
```

## Education
* Tbilisi State University

## Experience
No official experience

## Languages
* Russian(Native Speaker)
* Georgian(Native Speaker)
* English(B1-B2)
