# STL LIBRARY NOTES FOR C AND C++ PART 2
___

## SET (ordered) : 
ex. ques : Print all the unique elements in an array.  
Prog :  
```cpp
ar={1,2,1,4,4,5,2};

set<int> st; // declaring a set
int n=ar.length();

//INSERTION

for(int i=0;i<n;i++)
{
    st.insert(ar[i]); // adding elements to set.
}

// *****************
// DELETION
st.erase(s.begin()+3);// basically, st.erase(iterator);  

st.erase(s.begin(),s.begin()+3); // basically, deleting a range but upper bound is not included.

st.erase(5); // st.erase(value_in_set)

//*******************
//OTHER FUNCTIONS

auto it=st.find(5);// this function gives the iterator to a particular value.
// ans. iterator of 5

auto it=st.find(9);// If the value given in find function is not in the set , iterator returned is st.end() .
```
__Some Points__  
* Set in stl works similar to set in python.  
* Set only stores the unique element single time.  
* Set store values in a sorted structure basically in a linearly ascending fashion.  
* __Time complexity of insertion operation is ___O(log(N))___ times.__  
* __Time complexity of deletion operation is ___O(log(N))___ times.__  
* __Time complexity of range deletion operation is ___O(log(N))___ times.__ 
* We cannot use directly st[0], but will have to use iterators to call the value ex. st.begin() ,st.begin()+3 ,st.end()-2  etc.  

* Everything learned in vector mostly works with set also.

___
## SET (unordered) :

* IN UNORDERED set , we would never know what might be the order of our elements, it could be anything and hence the name.
* All the operations are same as that of ordered set.  
* The best advantage of unordered set over an ordered set is :   
    1. Best case time complexity : O(1)  
    2. Worst case time complexity : O(set size) i.e O(N)

    If we are not required to store our elements in ascending order in usecase , always use unordered set.

    If you encounter tle, switch to ordered set.  

* Average __time complexity__ is o(1).

___
## MULTISET : 
Basically multiset helps you to store all the elements (even if repeating) in a sorted fashion.  

```cpp
multiset<int> ms;
ms.insert(1);
ms.insert(2);
ms.insert(1);
ms.insert(3);
ms.insert(1);
ms.emplace(2); // emplace works same as insert
// ms= {1,1,1,2,2,3}

ms.erase(1);// this will erase all the instances of value ,here 1.
// ms = {2,2,3}

auto it= ms.find(2); // returns the iterator of the first element value 2.

ms.count(2); // returns the count of 2.
```  
* Complexity is o(Log N)
* Other functions are mostly same as set.
___
## MAP : 
#### This is just like dictionaries in python.

```cpp
map<string,int> m;
m["one"]=1;
m["two"]=2;
m["three"]=3;

// OR

m.emplace("four",4);

// DELETION 
m.erase("one");// m.erase(key);

m.erase(m.begin(),m.begin()+2);// erases the range

auto it = m.find("three"); //this iterator points to where the three lies.

m.empty(); // checks if this is empty or not.

//PRINTING KEY VALUE PAIRS

//Approach 1
for(auto it:m){
    cout<<it.first<<" : "<<it.second<<endl;
}

//Approach 2
for(auto it=m.begin();it!=m.end();it++)
{
    cout<<it->first<<" : "<<it->second<<endl;
}
```  

* Map just like set stores everything in sorted order (Linearly ascending fashion BY KEYS NOT VALUES).  
* If same key is used to store a different value , it overwrites the previous value.  
* When called the iterator , it.first and it.second, will automatically be recognised as key and then value at that pointer value.  
___
## UNORDERED MAP : 
  
Map which is unordered obviously.

Almost all the functions are repeated from map.  
__Almost all cases we get , time complexity = O(1) and worst case is O(N).__  

____
## PAIR Class :  

```cpp
pair<int,int> pr={1,2};
pair<pair<int,int>,int> pr = {1,{1,2}};
cout<<pair.first<<" and "<<pair.second.first<<endl;// = 1 , 1

pair<pair<int,int>,pair<int,int>> pr={{1,2},{3,4}};
cout<<pair.second.first<<endl; // = 3.
```
* While printing or calling if a nested pair ,{1,{3,4}}, pr.second wont work, you can get pr.second.first but not the whole pair.  
____
## MULTIMAP :  
```cpp
multimap<string,int> m;
m.emplace("hello",1);
m["hello"]=2;
```  
* Multimap stores multiple same key- different value pairs.
* Stores in linear ascending fashion in key.  
* Functions are almost same.  
___
## STACKS : 
#### This is a data structure which works on the principle of lifo, i.e last in first out.
ex. Books kept on one another.

#### FUNCTIONS :
1. pop
2. top
3. size
4. empty
5. push and emplace (same)  

```cpp
stack<int> st;
st.push(1);
st.push(3);
st.push(5);
st.push(7);

//st = 1,3,5,7
st.top(); // = 7
st.pop(); // = 7
st.pop(); // = 6
st.top(); // = 5

st.size(); // Number of elements in stack  

```
* Internal Implementation : Array and linked list.  
* Clear function in this doesnot exist.  
* Stack if empty, st.top throws an error , do remember this.  
___
## QUEUES :  
#### This is a fifo operation i.e first in first out.

#### FUNCTIONS :  
1. push  
2. front  
3. pop  
4. size  
5. empty  

* Mostly all functions are same as stacks with simple change of process, instead of lifo , we use fifo structure.  
* Time complexity of every function call : O(k)   
_____
## PRIORITY QUEUES :  
#### Stores all the values in sorted order and in time complexity O(n).  

* So as we go pushing values into PQ , it automatically stores accordingly in a sorted order.

```cpp
priority_queue<int> p;
p.push(3);
p.push(2);
p.push(9);
p.push(1);

p.top() // = 9
// p is stored as 9,3,2,1.
```
* For storing in ascending order , we can store its negetive value and then at the time of calling make it positive again.  
This is approach 1.

* Approach 2,  
```cpp
priority_queue<int,vector<int>,greater<int>> pr;

// everything pushed into pr will be stored in ascending order.
```  
_____
## DEQUEUE :  

Exactly similar to vector with some extra useful functions.

#### FUNCTIONS :  
1. push_front()  
2. push_back()  
3. pop_front()  
4. begin,end,rend,rbegin 
5. size  
6. clear  
7. empty  
8. at  

#### There is list container also and all its functions are exactly same as above just with a time complexity of o(1).