# Big O Notation - Baeldung

`Disclamer`: The present study has been based on a Baeldung page and the most part is replicated from there. Some small intepretation will be added but in general it is only for review purpose and for my personal lib.

[Source](https://www.baeldung.com/java-algorithm-complexity)

Algorithm analysis answers the question of `how many resources`, such as `disk space or time`, an algorithm consumes.

> Time taken per input size.

## Constant time - O(1) - quickest

```java
int n = 1000;
System.out.println("Hey - your input is: " + n);
```

```java
int n = 1000;
System.out.println("Hey - your input is: " + n);
System.out.println("Hmm.. I'm doing more stuff with: " + n);
System.out.println("And more: " + n);
```

We denote constant time algorithms as follows: `O(1)`. 

> Note that O(2), O(3) or even O(1000) would mean the same thing.

## Logarithmic time - O(log n) - 2nd quickest

What is important here is that the running time grows in proportion to the logarithm of the input (in this case, log to the base 2):

```java
for (int i = 1; i < n; i = i * 2){
    System.out.println("Hey - I'm busy looking at: " + i);
}

// output
Hey - I'm busy looking at: 1
Hey - I'm busy looking at: 2
Hey - I'm busy looking at: 4
```

We denote as `O(log n)`.

## Linear time - O(n) - 3rd quickest

If we say something grows linearly, we mean that it grows directly `proportional to the size of its inputs`.

```java
for (int i = 0; i < n; i++) {
    System.out.println("Hey - I'm busy looking at: " + i);
}
```

or 

```java
for (int i = 0; i < n; i++) {
    System.out.println("Hey - I'm busy looking at: " + i);
    System.out.println("Hmm.. Let's have another look at: " + i);
    System.out.println("And another: " + i);
}
```

The runtime would still be linear in the size of its input, n. We denote linear algorithms as follows: `O(n)`. 

> O(2n+1) = O(n).

## N log N time - O(n log n) - 4th quickest

n log n is the next class of algorithms. The running time grows in proportion to n log n of the input:

```java
for (int i = 1; i <= n; i++){
    for(int j = 1; j < 8; j = j * 2) {
        System.out.println("Hey - I'm busy looking at: " + i + " and " + j);
    }
}
```

For example, if the n is `8`, then this algorithm will run `8 * log(8)` = 8 * 3 = `24 times`.

## Polynomial time - O(n^P) - 5th quickest

> What's important to know is that O(n2) is faster than O(n3) which is faster than O(n4), etc.

```java
for (int i = 1; i <= n; i++) {
    for(int j = 1; j <= n; j++) {
        System.out.println("Hey - I'm busy looking at: " + i + " and " + j);
    }
}
```

This algorithm will run 8^2 = `64 times`.

## Exponential time - O(k^n)

Now we are getting into dangerous territory; these algorithms grow in proportion to some factor exponentiated by the input size.

> e.g. O(2n) algorithms double with every additional input.

> e.g. O(3n) algorithms triple with every additional input, O(kn) algorithms will get k times bigger with every additional input.

```java
for (int i = 1; i <= Math.pow(2, n); i++){
    System.out.println("Hey - I'm busy looking at: " + i);
}
```

This algorithm will run 2^8 = `256 times`.

## Factorial time - O(n!)

A classic example of this is solving the `traveling salesman` problem using a brute-force approach to solve it.

```java
for (int i = 1; i <= factorial(n); i++){
    System.out.println("Hey - I'm busy looking at: " + i);
}
```

Factorial(n) simply calculates n!. If n is 8, this algorithm will run `8! = 40320 times`.

## Asymptotic Functions

> Big O is what is known as an asymptotic function.
- Big O is useful to determine performance of an algorithm at its limit.
- It considers the worst case
