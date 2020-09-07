# BigO notation

Big O notation is used in Computer Science to describe the performance or complexity of an algorithm.

`Disclamer`: The present study has been based on a DeveloperInsider page and the most part is replicated from there. Some small intepretation will be added but in general it is only for review purpose and for my personal lib.

[Source](https://developerinsider.co/big-o-notation-explained-with-examples/)

## O(1) - constant time

The execution time not depend of the input. "This function runs in `O(1)` time (or __constant time__) relative to its input." 

```java
void printFirstArrayElement(int arr[]){
    printf("The first element of the array is:", arr[0]);
}
```

## O(n) - linear time

The execution depends of the input, where `n` is the _number of items_ in the array. "If the array has __10 items__, we have to __print 10 times__. If it has __1000 items__, we have to print __1000 times__."

```java
void printAllElementsArray(int arr[], int size){
    for (int i=0; i<size; i++){
        printf("%d\n", arr[i]);
    }
}
```

## O(n^2) - quadratic time

The execution depends of the input. If the input has 10 items, the outer loop will run `10 times` and the inner loop will also run `10 times` in each interation of the outer loop. "Thus this function runs in O(n^2) time (or "quadratic time"). If the array has 10 items, we have to print 100 times. If it has 1000 items, we have to print 1000000 times."

```java
void printAllPossibleOrderedPairs(int arr[], int size){
    for (int i=0; i<size; i++){                     //  n+1
        for (int j=0; j<size; j++){                 //  (n+1)*(n+1) = n^2 + 2n + 1
            printf("%d | %d\n", arr[i], arr[j]);    //  n^2
        }
    }
    // (n+1)*(n+1) = n*n + 1*n + n*1 + 1 * 1 = n^2 + 2n + 1
}
```

## O(2^n) - exponential

The execution depends of the input. "O(2^n) denotes an algorithm whose growth doubles with each addition to the input".

```java
int fibonacci(int num){
    if (num <= 1) return num;
    return fibonacci(num-2) + fibonacci(num-1);
}
```

## Drop the constant

```java
void printAllItemsTwice(int arr[], int size)
{
    for (int i = 0; i < size; i++)          //  n+1
    {
        printf("%d\n", arr[i]);             //  n
    }
	
    for (int i = 0; i < size; i++)          //  n+1
    {
        printf("%d\n", arr[i]);             //  n
    }

    // (n+1) + (n+1) = 2n + 2 = 2n = n ==> O(n) reducing the constants
}
```

The exaple above is a `O(2n)` complexity, which can be expressed by only `O(n)`.

```java
void printFirstItemThenFirstHalfThenSayHi100Times(int arr[], int size)
{
    printf("First element of array = %d\n",arr[0]); //  1
	
    for (int i = 0; i < size/2; i++)                //  n/2 + 1
    {
        printf("%d\n", arr[i]);                     //  n/2
    }

    for (int i = 0; i < 100; i++)                   //  100
    {
        printf("Hi\n");                             //  100
    }

    // 1 + (n/2 + 1) + 100 = n/2 + 102 = n/2 ==> O(n)
}
```

## Drop less significant term

```java
void printAllElementAndEachPairs(int arr[], int size){
    for (int i=0; i<size; i++){                     // n + 1
        printf("%d\n", arr[i]);                     // n
    }

    for (int i=0; i<size; i++){                     // n + 1
        for (int j=0; j<size; j++){                 // (n + 1)*(n + 1) = n^2 + 2n + 1
            printf("%d | %d\n", arr[i], arr[j]);    // (n*n) = n^2
        }
    }
}
```

In the case above we would have: `O(n^2 + n)`. Removing the less significant term, it is equal to `O(n^2)`. "We can get away with this because the less significant terms quickly become, well, less significant as n gets big". Similarly:

O(n^3 + 50n^2 + 10000) is `O(n^3)`
O((n + 30) * (n + 5)) is `O(n^2)`

## Worst case

"In general we'd say this is `O(n)` runtime and the "worst case" part would be implied. But to be more specific we could say this is worst case `O(n)` and best case `O(1)` runtime. For some algorithms we can also make rigorous statements about the "average case" runtime."

```java
bool arrayContainsElement(int arr[], int size, int element)
{
    for (int i = 0; i < size; i++)
    {
        if (arr[i] == element) return true;
    }
    return false;
}
```

## Proving BigO

__f(n) = O(g(n))__ if `c` and some initial value `k` are positive when `f(n) <= c * g(n)` for all `n > k` is true.

"What we're basically saying here is that no matter our input (n), it must be greater than or equal to our constant (c) when the size of our input (n) is more than another constant value (k), in our case the iteration count of the function."

## Disproving BigO

```java
void print_values_with_repeat(int end) //end = 100 
{
    for (int i = 0; i < end; i++)  //Execution count: 100
    {
        for (int j = 0; j < end; j++)  //Execution count: 10000
        {
            printf("i = %d and j = %d\n", i, j); // Execution count: 1
        }
    }
}
```

Is `print_values_with_repeat` O(n)? No.

| N	| F(N) | G(N) | TRUE/FALSE | 
| --- | --- | --- | --- |
| 0	| 0	| 0	| False |
| 1	| 1	| 1	| True |
| 2	| 4	| 2	| False |
| 3	| 9	| 3	| False |


Suppose our constant c is 1, 1 <= 1 * 1 for 1 > 0, this is true - however our definition says that g(n) must be greater than all values of f(n).

So if we take the value 2 of n, 2 <= 1 * 4 for 1 > 0, we can see that this is now false, which disproves our hypothesis that print_values_with_repeat is O(n). Even if we change our constant c to 2, this would still prove false eventually.

Is `print_values_with_repeat` O(n^2)?

| N	| F(N) | G(N) | TRUE/FALSE | 
| --- | --- | --- | --- |
| 0	| 0	| 0	| False |
| 1	| 1	| 1	| True |
| 2	| 4	| 4	| True |
| 3	| 9	| 9	| True |




