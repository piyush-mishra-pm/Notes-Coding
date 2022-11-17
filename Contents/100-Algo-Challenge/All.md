# 100 Algorithms Challenge (Dylan Israel)

### 1: absoluteValuesSumMinimization
Given a sorted array of integers a, find an integer x from a such that the value of

    `abs(a[0] - x) + abs(a[1] - x) + ... + abs(a[a.length - 1] - x)`
is the smallest possible (here abs denotes the absolute value).
If there are several possible answers, output the smallest one.

Summary: Return median, and decide the median value based on whether even or odd length array.

```typescript
function absoluteValuesSumMinimization(arr:number[]):number{
    const isEvenLengthArray = arr.length;

    return isEvenLengthArray ? 
        arr[arr.length/2 - 1] :
        arr[Math.floor(arr.length/2)];
}

```
---

### 2: Add indefinite number of values:
Write a function that returns the sum of all numbers regardless of # of params.
```typescript
function addIndefinite(...nums:number[]):number{
    let sum = 0;
    forEach((n)=>{
        sum+=n;
    })
    return total;
}
```

---
### 3: Add Rectangular border to arrays of text:
Given a rectangular matrix of characters, add a border of asterisks(*) to it.

**Example**

For

    picture = ["abc",
           "ded"]
the output should be

    addBorder(picture) = ["*****",
                      "*abc*",
                      "*ded*",
                      "*****"]

```typescript
function addBorder(words:string[]):string[]{
    const horizontalBorder = "*".repeat(words[0].length+2);

    // adding horizontal borders: top and bottom:
    //  Top border:
    words.unshift(horizontalBorder);
    //  Bottom border:
    words.push(horizontalBorder);

    // adding Vertical borders: * on both ends of each word.
    for(let i=1; i<words.length-1; i++){
        words[i] = "*".concat(words[i],"*");
    }

    return words;
}
```

---
### 4: Add the digits in a number:
You are given a positive number n. Return the sum of its digits.

**Example**

For n = 29, the output should be
addTwoDigits(n) = 11.

```typescript
function addDigitsInNumber(n: any): number {
    const digitCharArray = n.toString().split('').map(i=>parseInt(i));

    return digitCharArray.reduce((total: number, current: number) => {
return total+current;
    },0);
}
```
---

### 5. Largest adjacent pair product:

Given an array of integers, find the pair of adjacent elements that has the largest product and return that product.

**Example**

For inputArray = [3, 6, -2, -5, 7, 3], the output should be
adjacentElementsProduct(inputArray) = 21.

7 and 3 produce the largest product.

```typescript
function(arr:number[]):number{
    let largestProduct= arr[0]*arr[1];
    for(int i=2; i<arr.length ; i++){
        largestProduct = Math.max(arr[i]*arr[i-1],largestProduct);
    }
    return largestProduct;
}
```
