# Reduce


- This afternoon we are going to talk about Reduce
- Firstly - A mini recap on some the HOFs you've worked with so far.

- Both Map and Filter are HOFs. 

> Why do we call them HOFs?
  - Because they take a function as an argument. 
  - M&F are also array transformations. since they transform a starting array into a new array with new contents


> Can anyone describe when we might want to use a Map?
  -  we would use map if we wanted every item in that array to be tranformed in some way
  - result to be the same length as the original

> When might I want to use Filter?

  - To break down original array to a shorter more refined result
  - rather than transforming every item in the array
  - When I want filter the array contents based on whether each element passes a condition
  - iteratee function
  - predicate function

```
const nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
```

> If i wanted every item in this array to be multiplied by 3

> what array method might i use?

> How would i do that?

```
const tripledNums = nums.map(function (num) {
  // ? args
  // ? What do we call the function that map takes
  return num * 3;
});

console.log(tripledNums);
```

> what do we call the function that map takes?
  - iteratee function
  - this is because on each iteration of the nums array, it will invoke this function



> Can anyone tell me what function i would use if i wanted to only return even nums

  -  filter
  
> why this a good option?

```
const evenNums = nums.filter(function (num) {
  if (num % 2 === 0) return true;
  else return false;
});

console.log(evenNums);
```

> ok. we happy?

> so what happens if we want to do both at once?

> maybe we wanted to introduce even more functionality to each iteration

```
const evenTripledNums = nums.map(num => {
  return num * 3;
}).filter(num => {
  return num % 2 === 0;
});
console.log(evenTripledNums);
```

> why is this not the best way to work out result?

- too verbose
- we loop over the array more than once

> What method might we use to combine this into one?

## Introducing Reduce.

- the previous array transformations havent provided us with a great deal of flexibility
- map
  - we are forced to return an array 
  - and forced to handle each item the same way

- filter
  - we can only decide to keep or lose an item
  - nothing more

- reduce allows logic to be more flexibility

-  Lets refactor the above code with reduce..





### REDUCE EXAMPLE

```
const reducedTripleEvenNums = nums.reduce(function (acc, num) {
  if (num % 2 === 0) acc.push(num * 3);
  return acc;
}, []);

console.log(reducedTripleEvenNums);
```

- Reduce takes 2 args
  - an iteratee function as an argument
  - starting accumulator

- The iteratee func differs (key difference)
  - accumulator
  - As well as...
    - current value
    - index
    - array


- An accumulator can be anythin we wish it to be (within reason)
  - array
  - object
  - string
  - number

- Its name refers to the fact that it accumulates return values from each return statement of the function

- this is just one example of how flexible reduce is

- we can of course implement functionality from multiple array methods within it to produce the same results

> HAPPY?

- However the **most common use** of reduce is to iterate over an array to produce
- **output** of **different data type** altogether

```
const nums = [1, 2, 3, 4, 5];
```

> what if i wanted to sum up all the contents of my nums array

> how would i do this?

### EXAMPLE

```

const sum = nums.reduce((total, num) => {
return total += num;
}, 0)

```

> how many args for reduce? 
  - iteratee
  - initialAcc

> whats the first argument to iteratee?

 - so i can rename my accumulator total/sum since it best describes what it is

> whats my result?

```
console.log(sum);
```

- lets look into it in a little more depth

- on each iteration the function is called with the current total and num

### CONSOLE LOG INSIDE FUNCTION

- the iteratee function takes more than just 2 args

- it also takes the index position it's on and also a reference to the arr

- the last argument is very rarely used. And in my experience if youre using it you might be going down a rabbit hole with your solution



```
const sum = nums.reduce((total,num,index, arr) => {
    console.log(total, num)
    total = total + num;
    return total
  }, 0)

console.log(sum);
```

- lets walk through what reduce does to create our sum

### DRAW TABLE

-  on the first iteration what arguments does it get..
- ...
- on our final iteration we get the return of the final invokation of out function


> what happens when i remove the return statement?

```
const users = [{name: 'paul', loggedInRecently: false}, {name: 'liz', loggedInRecently: false}, {name: 'jonny', loggedInRecently: true}]


// ['paul', 'jonny]

// array to obj

const result = users.reduce((acc, user) => {
  
}, {})

```

> QUESTIONS????!!!!
