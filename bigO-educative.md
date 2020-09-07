# BigO Notation - Educative

`Disclamer`: The present study has been based on a Educative page and the most part is replicated from there. Some small intepretation will be added but in general it is only for review purpose and for my personal lib.

[Source](https://www.educative.io/blog/a-big-o-primer-for-beginning-devs?aid=5082902844932096&utm_source=google&utm_medium=cpc&utm_campaign=blog-dynamic&gclid=CjwKCAjwkdL6BRAREiwA-kiczJao6VqwAavndC26wrtTqQhT5oHIFNT_zgqfBBfzB2db9aDeMRlSjRoCrcQQAvD_BwE)

BigO Notation is a mathematical function used to determine the execution time required by an algorithm. 

There are two kinds of `complexities`: __time__ and __space__. Time complexity and space complexity are essentially approximations of how much time and how much space an algorithm will take to process certain inputs respectively.

- `Best case` — represented as Big Omega or Ω(n)
- `Average case` — represented as Big Theta or Θ(n)
- `Worst case` — represented as Big O Notation or O(n)

> “well, in the worst case scenario, my algorithm will scale this quickly”.

## O(1) - Constant time complexity

e.g.
- Array: inserting or retrieving an element

## O(log n) - Logarithmic time complexity

It is O(log n) when we use divide and conquer algorithms e.g binary search.

e.g.
- Binary tree: inserting or retrieving an element

## O(n) - Linear time complexity

- When performance will grow linearly and in direct proportion to the size of the input

e.g.
- Tree: Depth first search (DFS) of a tree

## O(n²) - Quadratic time complexity

As the elements in your list increase, the time it will take for your algorithm to run will increase exponentially.

e.g.
- Sorting algorithm: Bubble sort and insertion sort

## Asymptotic Analysis

- Drop the leading constants  
- Ignore the lower order terms

e.g.
- Find the Big O complexity of an algorithm with the time complexity 3n³ + 4n + 2. ==> `O(n³)`

```c++
#include <iostream>
using namespace std;
int main(){
 int n = 10;                // 1
 int sum = 0;               // 1
 for (int i=0; i<n; i++)    // n+1
   sum+=2;                  // n
 cout << sum;               // 1
 return 0;
}

// 1 + 1 + n+1 + n + 1
// 2n + 3 ==> O(n)
```

### General tips for asymptotic analysis:

- Every time a list or array gets `iterated over c x length times,` it is most likely in O(n) time.
- When you see a problem where the number of elements `in the problem space gets halved (dividido pela metade) each time`, it will most probably be in O(logn) runtime.
- Whenever `you have a singly nested `loop, the problem is most likely in quadratic time.

## O(1)
```c++
void printFirstItem(const vector<int>& items)
{
    cout << items[0] << endl;
}
```

## O(n)
```c++
void printAllItems(const vector<int>& items)
{
    for (int item : items) {
        cout << item << endl;
    }
}
```

## O(n^2)
```c++
void printAllPossibleOrderedPairs(const vector<int>& items)
{
    for (int firstItem : items) {
        for (int secondItem : items) {
            cout << firstItem << ", " << secondItem << endl;
        }
    }
}
```

## Big O Notation cheat sheet

![](https://github.com/armbrustsamuel/bigO-notation-review/blob/master/img/img-2.png)

![](https://github.com/armbrustsamuel/bigO-notation-review/blob/master/img/img-3.png)

![](https://github.com/armbrustsamuel/bigO-notation-review/blob/master/img/img-4.png)

![](https://github.com/armbrustsamuel/bigO-notation-review/blob/master/img/img-1.png)