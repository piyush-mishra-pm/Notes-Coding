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
---
### 6. Longest Words from Word Array:
Given an array of strings, return another array containing all of its longest strings.

**Example**

For inputArray = ["aba", "aa", "ad", "vcd", "aba"], the output should be
allLongestStrings(inputArray) = ["aba", "vcd", "aba"].

```typescript
function getLongestWordsFromWordArray(words: string[]): string[]{
    let longestWordLength = 0; // Assuming empt word as longest.
    const longestWords = [];

    words.forEach(word=>{
        // skip if word is shorted than longestWord found so far.
        if(longestWordLength>word.length){
            return;
        }
        // clean up if longest word so far is shorter than current word.
        else if(longestWordLength<word.length){
            longesWords = [];
            longestWordLength=word.length;
        }
        // Equal to largest wordlength, or largest word length so far shorter
        // than current word. In both cases, add to longestWord collection.
        longestWords.push(word);
    })

    return longestWords;
}
```
---
### 7. Almost Increasing Sequence:

Given a sequence of integers as an array, determine whether it is possible to obtain a strictly increasing sequence by removing no more than one element from the array.

**Example**

- For sequence = [1, 3, 2, 1], the output should be
almostIncreasingSequence(sequence) = false;

There is no one element in this array that can be removed in order to get a strictly increasing sequence.

- For sequence = [1, 3, 2], the output should be
almostIncreasingSequence(sequence) = true.

You can remove 3 from the array to get the strictly increasing sequence [1, 2]. Alternately, you can remove 2 to get the strictly increasing sequence [1, 3].

```typescript
// If a drop happens, then just remove the max of drop causing numbers.
// Will ensure that minimum of them remains, and help next sequence elements
// be greater than itself.
// sequence: 2,4,1,5 => remove 1 (or replace by 4) as 1<2
// sequence: 2,4,3,5 => remove 4, as 3>2.
// Also see: https://leetcode.com/problems/remove-one-element-to-make-the-array-strictly-increasing
function almostIncreasingSequence(nums:number[]):boolean {
    int numDrops = 0;
    int peakSoFar = nums[0];
    for (int i = 1; i < nums.length && numDrops < 2; ++i) {
        if (peakSoFar >= nums[i]) {
            ++numDrops;
            if (i > 1 && nums[i - 2] >= nums[i]) {
                peakSoFar = nums[i - 1];
                continue;
            }
        }
        peakSoFar = nums[i];
    }
    return numDrops < 2;
}
```
