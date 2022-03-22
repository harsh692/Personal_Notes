# STL LIBRARIES NOTES FOR C AND C++
## By STRIVER....
____

## STL
1. Container : a storage facility
2. Iterator : a traversing tool
3. Algorithm : predefined logic to get some targeted algorithms

## Basic
1. Header file
```c++
#include <bits/stdc++.h>
using namespace std;
```  
* first line is a header file which is used to import all the packages and containers.  
This mostly contains all packages and therefore should not be used in industry since there, we have to use specific containers and functions.

* if we wont write namespace std,  
we will have to write in this format :  
```c++
std:vector<int> a(3); 
 ```
 Another use:  
 ```c++
  namespace harsh{
      int a=10;
      int getvalue()
      {
          return 5;
      }
  }
  int main()
  {
      double a=20.0;
      cout<<a<<endl; //prints 20.0
      cout<<harsh::a<<endl; // prints 10
      cout<<std::getvalue()<<endl;
  }
 ```  
 Answer : 20.0
 if not used namespace then would have given the error that two definition is defined.  

## Struct
This is a type of container which when definded is a separte data type in itself.

```c++
struct node{
    int a;
    char b;
    string c;

    //For approach 2
    // constructor definded for initializing an object of node type  
    node(x,y,z)
    {
        a=x;
        b=y;
        c=z;
    }
}

int main()
{
    //approach 1
    node one;
    one.a=2;
    one.b='c';
    one.c="hello";

    //approach 2
    node two = new node(2,'c',"hello");

}
```
Always the second approach is considered better practise. Even in interview.  
You can use any type of data inside a struct ex. __Array[] , int , double__ etc.  

## Arrays :
 This is not that much.

 IF defind inside main scope, an array is initialised with garbage or null values.  
 BUT when defined in global scope, they are initialised with default values of type.

 ```c++
array<int,5> a; 

std::array<int,5> b; //if not used namespace

array<int,5>a = {1,2,3}; // automatically will be initialised with 0 in the remaining places.

int arr[1000]={0};//first is initialised with 0, and rest all are a initialised with 0 by itself.

 ```
### Functions

```c++
a.fill(1); // fills whole array with single value  
a.at(index) // same as a[index];
a.size() // size of array
```

### Iterator
* Data saved in an array is always saved in _contiguous_ memory location.
* contiguous = continuous, therefore if we know the adress of first data in container like array, we can traverse through it.
* We have:  
    1. begin() : Points to the first data adress.
    2. end() : Points to the data adress after the last data.
    3. rbegin() : Points to the last data memory adress.
    4. rend() : Points to the memory adress just before the first data adress.

Example :  
```c++
array<int,4> a={1,2,3,4};
for(auto it:a.begin();it!=a.end();it++)
{
    cout<< *it <<endl; // it is a pointer therefore we just have to get its value by *it.
}

for(auto it:a.rbegin();it!=a.rend();it++)
{
    cout<< *it <<endl; // Reverse Print
    // it should not be it--, here since its a pointer ,it will automatically move backwards when it++ is written.
}

for(auto it:a.end()-1;it>=a.begin;it--)
{
    cout<< *it <<endl; // Reverse order approach 2
    }

for(auto it:a)
{
    cout<<it<<endl;
}// this acts like for-each.
// this will separately give one value at a time and then move forward , another approach for traversing with iterator.
for(auto it:str){
    cout<<it<<endl; // hello= h,e,l,l,o
}
```
## Vector :  
__Max size__ of an array in main block : 10^6  
__Max size__ of an array in global scope : 10^7
If Boolean datatype , __Max size__ : 10^8

SAME IS THE CASE FOR VECTOR AS ABOVE.
IF we exceed the space , we get error :  
SEGMENTATION ERROR........

__Vector__ : __Dynamic array__ ,with each initialisation after declaration, size increases.  
### Functions : 
```cpp
vector<int>a;
a.push_back(3); // adds an element from back
a.pop_back(); // deletes last element.
a.emplace_back(4); // identical to pushback but takes LESSER TIME.
```
* There are other functions such as upper bound, lower bound, begin, end , rend,rbegin , swap etc.
* Even if we have defined a vector with inititalise memory like :
    ```cpp
    vector<int>b(4,0) // = {0,0,0,0}
    ```
    we can still push back in this vector.
* COPYING all the elements of a vector to a new vector:  
    ```cpp
    vector<int> c(a.begin(),a.end())//copies from first to last element through iterator.
    vector<int> d(a) // copies entire vector.
    ```
* Two dimenstional array :  
    ```cpp
    vector<vector<int>> ar;

    vector<int> a;
    a.push_back(1);
    a.push_back(2);

    vector<int> b;
    b.push_back(3);
    b.push_back(4); 

    ar.push_back(a);
    ar.push_back(b);

    for(auto it:ar)
    {
        for(auto it2:it)
        {
            cout<<it<<endl;
        }
    } 
    // we can also write in traditional way like,
    // ar[i][j] but it is two long to write, so your choice.

    vector<vector<int>> br(10,vector<int> (20,0))  
    // br is a 2d vector with size 10 and elements as vectors of size 20 and value 0.
    ```
*  Two dimensional array apprach 2

    ```cpp
    vector<int> arr[10];
    // array is definded of type vector as elements and const. size 10.
    arr[0];// this is an empty vector.
    ```