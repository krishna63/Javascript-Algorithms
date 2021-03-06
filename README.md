# Javascript Algorithms
---

###### 1. Write an algorithm for the below problem statement.

```
 There are 8 houses in a row. Some houses are empty and some are not, it will be represented with 1 and 0. 
 
 On Day 1 let’s say first 3 houses are active so it will be represented like [1 1 1], 
 
 On day 2
 - For 1st house, his neighbors are empty (0) and active (1) on previous day so he will be active (1), 
 - For 2nd house, both neighbors are active (1) on previous day so he will be passive (0)
 - For 3rd house, his neighbors are active (1) and empty (0) on previous day, so he will be active (1). 
 
 So day 2 status for first 3 houses will be [1 0 1].  
 
Example:
Sample Input:  [1 0 1 1 0 0  1 0]
Sample Day 1 Output -> [1 0 1 1 0 0 1 0]
Sample Day 2 Output -> [0 0 1 1 1 1 0 1]
Sample Day 3 Output -> [0 1 1 0 0 1 0 0]
Sample Day 4 Output -> [1 1 1 1 1 0 1 0]
Sample Day 5 Output -> [1 0 0 0 1 0 0 1]

Now, write an algorithm to find out the status of each house on any given day. 
Example: findStatus([1,1,1,0,1,0,1,0], 5)

```


<details>
<summary>Answer...</summary>
<p>

```
 const findStatus = (arr, day) =>{
  return (day === 1) ? arr : findStatus(checkStatus(arr), day-1);
 };
 
 const checkStatus = arr => {
  return arr.reduce((a,c,i)=>{
    return (arr[i-1] === arr[i+1]) ? [...a, 0] : [...a, 1]
  },[]) 
 };
 
 findStatus([1,1,1,0,1,0,1,0], 5) = > output: [1, 0, 1, 0, 1, 0, 0, 1]
```

</p>
</details>  

###### 2. Write an algorithm to remove all duplicates and non repeated values from an array.

```
Sample Input:  [1, 1, 2, 3, 3, 3, 4, 2, 5, 5]
Sample output: [1, 2, 3, 5] (4 not repaeated in the input array)
```

<details>
<summary>Answer...</summary>
<p>

```
const getArray = arr => arr.sort((a,b)=>(a-b)).reduce((a,c,i,ar)=>{
  return (!a.includes(c) && (ar[i-1] === c || ar[i+1] === c)) ? [...a, c] : [...a]
},[])
```

In the above code apart for checking unique values using array reducer, 
we're also checking if the main array previous or next index has same values. 
This way we can includes only repeated values from main array.

</p>
</details>  
