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