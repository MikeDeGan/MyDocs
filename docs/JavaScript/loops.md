# Loops in JavaScript

Author: Lilian Lin

[Original Medium Article](<https://medium.com/@linlinghao/loops-in-javascript-6aeed4a2c343>)

Loops in JavaScript means a chunk of codes executed repeatedly in certain amount.

For example, if we want to print “Hello” in console for 5 times, we can write the following statements:

```
console.log('Hello');
console.log('Hello');
console.log('Hello');
console.log('Hello');
console.log('Hello');
```

### for…loop

Seems like too much. This is the time when loops jump in. Just need to write the statement one time, give it a condition, then the statement can be executed repeatedly while the condition evaluates to true.

```
for(let i = 0; i < 5; i++){
  console.log('Hello');
}
```

**for loops** is the most basic one in JavaScript, we can see it as a counter. It requires 3 statements in parenthesis:

1. Initialize the counter: **let i=0** (the counter starts from 0)**.**
2. Condition, which tells the **for loop** when to stop: **i < 5** (when i reaches 5, the condition evaluates to false, the loop stops running).
3. Increment or Decrement the counting: **i++** (starts from 0, each time increase 1. if you use — — , then the counter will decrease 1).

So each time computer will evaluate if the variable’s current value passes condition. If it is, run the code inside. If it’s not, stop the loops.

```
//
i = 0
i<5? true
'Hello'
i++ => i = 1
i<5? true
'Hello'
i++ => i = 2
i<5? true
'Hello'
i++ => i = 3
i<5? true
'Hello'
i++ => i = 4
i<5? true
'Hello'
i++ => i = 5
i<5? false
stop counting!
```

**for loops** are also often used on array:

```
const arr = ['H', 'E', 'L', 'L', 'O'];
for(let i = 0; i < arr.length; i++){
  console.log(arr[i]);
}
//in console will print:
H // i = 0, i < 5?true, i++, print arr[0]
E // i = 1, i < 5?true, i++, print arr[1]
L // i = 2, i < 5?true, i++, print arr[2]
L // i = 3, i < 5?true, i++, print arr[3]
O // i = 4, i < 5?true, i++, print arr[4]
// i = 5, i = arr.length false, stop
```

### for…of loops

There is also another loop that can iterate through an array. And with this one, you don’t need to create index variables. Once reaches the end of the array, it will stop looping automatically:

```
for(let val of arr){
  console.log(val);
}
//in console will print:
H
E
L
L
O // this is the last item in arr, stop looping.
```

But **for…of** loops only works with **iterable** values. So it can not be used on objects.

### **for…in** loops

This loop becomes very handy when working with objects. Imagine if you want to print a grocery list, but you are not sure how many items are in this list, so just iterating through it, and print them all.

```
const grocery = {
1: 'apple',
2: 'banana',
3: 'milk',
4: 'bread',
5: 'chicken',
6: 'pasta'
}
for(let item in grocery){
  console.log(item);
}
//in console will print:
apple
banana
milk
bread
chicken
pasta // this is the last item in grocery object, stop looping.
```

### **while loops**

Then how about we want looping for infinite times and break automatically under certain conditions. This is when **while loops** jump in:

```
let num = 5;
while(num<200){
  console.log(num);
  num = num*5;
}
//in console will print:
5 // num = 5, num < 200? true, print num, num*5
25 // num = 25, num < 200? true, print num, num*5
125 // num = 125, num < 200? true, print num, num*5
// num = 625, num < 200? false, stop looping
```

As we can see. The condition is evaluated before the statement in the loop is executed. If the condition returns true, the statement is executed and the condition is evaluated again. If the condition returns false, the statement will be stop executing.

### **do…while** loops

But sometimes we are not sure about what the condition will be returned. In case nothing is executing (the condition evaluates to false at the beginning), we can use **do…while** loops.

```
let num = 200;
do {
  console.log(num);
} while(num++ < 200)
//in console will print:
201 
// num++ = 201; num++ < 200? false stop looping
```

Have you noticed what’s the difference? **do…while** loops evaluate its condition after the execution of the given statement in the loop. So even though the condition returns false at the beginning of iterate, the statement will be executed **at least once**.

------

When we started learning **for loops**, we usually use it on arrays. However array as the ‘most iterable’ object, instead of passing it into for loops, we can also make use of build-in array method that offers more straight forward syntax to reach different goals.

I’d like to put those methods in two kinds:

1. iterate without returning a new array.
2. iterate and create a new array.

### **array.forEach()**

It will execute a function on every item in the array. **No new array will be returned**.

**forEach** method will take a function as its argument. When the function starts iterating, it will have access to three things about current item: **value***,* **index***,***object.**

```
const grocery = ['apple','banana','milk','bread','chicken']
grocery.forEach(function(value, index, object){
  console.log(value, index, object);
})
//in console will print:
apple 0 (5) ["apple", "banana", "milk", "bread", "chicken"]
banana 1 (5) ["apple", "banana", "milk", "bread", "chicken"]
milk 2 (5) ["apple", "banana", "milk", "bread", "chicken"]
bread 3 (5) ["apple", "banana", "milk", "bread", "chicken"]
chicken 4 (5) ["apple", "banana", "milk", "bread", "chicken"]
pasta 5 (5) ["apple", "banana", "milk", "bread", "chicken"]
```

But usually we just need the value argument to work on, and arrow function will make such method a cleaner syntax.

```
grocery.forEach(value => console.log(value))
//in console will print:
apple
banana
milk
bread
chicken
pasta
```

### **array.find()**

It will take a condition in the provided function, and return the **first element**that passes the condition. If nothing fulfills the condition, **undefined** will be returned.

```
const num = [1,2,3,4,5,6];
let smallNum = num.find(item => item < 3);
let bigNum = num.find(item => item > 6);
console.log(smallNum, bigNum);
//in console will print:
1 undefined 
// though 1,2 are both < 3, 1 is the first value passed the test, so only 1 is returned.
// no value in the num array is > 6, so undefined is returned.
```

### array.findIndex()

This method is similar with the **.find()** method, the only difference is that it returns the **index** of the first element that pass the condition. If no item passes the test, it returns **-1**.

```
const num = [1,2,3,4,5,6];
let smallIndex = num.findIndex(item => item < 3);
let bigIndex = num.findIndex(item => item > 6);
console.log(smallIndex, bigIndex);
//in console will print:
0 -1 
```

### array.some()

This method also takes a condition given by the function. It checks if **any**elements in the array pass the condition (**at least one**). It returns **true / false**.

```
const num = [1,2,3,4,5,6];
let isSmall = num.some(item => item < 3);
let isBig = num.some(item => item > 6);
console.log(isSmall, isBig);
//in console will print:
true false
```

### **array.every()**

It checks whether **all** elements in the array pass the condition. It returns **true / false**.

```
const num = [1,2,3,4,5,6];
let areSmall = num.every(item => item < 3);
let areBig = num.every(item => item > 6);
console.log(areSmall, areBig);
//in console will print:
false false
```

### array.reduce()

This is a really helpful and ‘fancy’ method.

It executes a provided function on each element of the array, and reduce the value of the array to **a single value**. The provided function must take two parameters:

\1. **accumulator**: it accumulates the returned value.
\2. **currentValue**: the element being processed in the array.

```
const num = [1,2,3,4,5,6];
let sum = num.reduce((accumulator, currentValue) => {
  return accumulator + currentValue;
})
console.log(sum);
// 
accumulator = 1, currentValue = 2, return 3
accumulator = 3, currentValue = 3, return 6
accumulator = 6, currentValue = 4, return 10
accumulator = 10, currentValue = 5, return 15
accumulator = 15, currentValue = 6, return 21
//in console will print:
21
```

### array.reduceRight()

It works exactly the same as .reduce() method, the only difference is it iterates an array backwards, from right to the left side.

```
const newNum = [1,10,100,1000];
let minus= newNum.reduceRight((accumulator, currentValue) => {
  return accumulator - currentValue;
})
console.log(minus);
// 
accumulator = 1000, currentValue = 100, return 900
accumulator = 900, currentValue = 10, return 890
accumulator = 890, currentValue = 1, return 889
//in console will print:
889
```

All the iterating methods above do not return a new array. But there are times we need our input data immutable, which means a new array should be created from the existing array. For example, in React Redux, we have to work on new datas, and the original data can not be mutated.

So let’s talk about the second type:

### array.map()

This method is similar with forEach(), which executes the given function on each item in the current array. And it creates **a new array** with the result of the provided function.

```
const num = [1,2,3,4,5,6];
let multiply = num.map(value => value * 2);
console.log(multiply);
//in console will print:
[2, 4, 6, 8, 10, 12]
```

### array.filter()

This method takes a condition in the provided function, and iterates through the array to check if each element passes the condition. Then it will **create a new array** with all the elements that passed the condition.

If none of the elements pass the condition, **an empty array** is created.This method is useful when you need to find one or more items based on a condition you create.

```
const num = [1,2,3,4,5,6];
let smallNums = num.filter(item => item < 3);
let bigNums = num.filter(item => item > 6);
console.log(smallNums, bigNums);
//in console will print:
[1,2] []
```

------

We’ve covered different loop functions above. But how do we choose which to use? Below are my own rules of thumbs:

1. Following the functional programming practices, given an array, we don’t want to mutate the original array, so definitely consider array method: like map(), filter().
2. If we simply want to iterate an array, array methods like forEach() can usually do what we want. forEach() can take a callback function with an arity of three and you can pass the element index to it.
3. If we want to iterate through all keys of an object, consider for…in loops.
4. If we want your statement run at least once, use do…while.
5. If any of above is not what we want, for loop always a fallback choice for us to customize our functions and conditions.

Above are my personal preferences about using loops in Javascript. In reality, situations are more complicated and nuanced, and require our judgement and team agreements to write the looping code. Don’t forget, the ultimate goal is to make our code expressive, so that it’s easy to read and maintain.

Using loops in JavaScript is like riding a rollercoaster, it seems to have a lot of different types. But no matter how it changes, the main idea never changes — iterate&run.

Enjoy your rides!


  