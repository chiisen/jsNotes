又稱展開運算符、Spread syntax，會將陣列展開成個別值灑進去。

## 用途 1 — 結合兩個陣列

```javascript
var arr1 = ['emma','is'];
var arr2 = [18,'years old'];
var combinedArr = arr1.concat(arr2);// 要結合兩個陣列，concat 會是一種常見的方式
console.log(combinedArr); // ["emma", "is", 18, "years old"]
```

```javascript
var arr1 = ['emma','is'];
var arr2 = [...arr1, 18,'years old'];
console.log(arr2); // ["emma", "is", 18, "years old"]
```

---

```javascript
var arr1 = ['emma','is'];
var arr2 = [18,'years old'];
var combinedArr = [...arr1, ...arr2];
console.log(combinedArr); // ["emma", "is", 18, "years old"]
```

```javascript
var arr1 = ['emma','is'];
var arr2 = [...arr1];
arr2.push(18, 'years old'); // 不會影響到 arr1
console.log(arr2);          // ["emma", "is", 18, "years old"]
console.log(arr1);          // ['emma', 'is']
```

---

## 用途 2 — 傳入函式作為參數

```javascript
function mySum(x,y){
  return x+y;
}
var arr = [1,2];
mySum.apply(null, arr)  // 3 - 要將陣列展開傳入函式，會用上 apply 這個方法
```

```javascript
function mySum(x, y){
  return x+y;
}
var arr = [1,2];
Sum(...arr);  // 3
```

## 用途 3 — 將可迭代 (literable) 的物件轉為陣列

```javascript
const name = 'emma';
const spreadName = [...name];
console.log(spreadName)  // ['e','m','m','a']
```

---

# 其餘運算子(Rest operator)

又稱為其餘運算符，可以將剩下的值集合成一個陣列。

## 用途 1 — 其餘參數 (Rest parameters)

```javascript
// 回傳參數加總
function sumUp(...nums){
  console.log(nums);  // 傳入的參數被組成陣列
  let total = 0;
  nums.forEach((number)=>{
    total += number;  // 將陣列內的數字加總起來
  })
  return total;       // 回傳 total
}
sumUp(1)     // [1],     1
sumUp(1,2,3) // [1,2,3], 6
```

```javascript
function many(x,y, ...z){ // 指定了兩個參數和一個剩餘參數
  console.log('x:',x);    // 印出 x
  console.log('y:',y);    // 印出 y
  console.log('z:',z);    // 印出剩餘參數 z
}
many('emma', 'is', 18, 'years', 'old');
// x: emma
// y: is
// z: [18,'years','old']  // 後面剩下的被組成一個陣列了
```

```javascript
many('emma', 'is', 'good')
// x: emma
// y: is
// z: ['good']
```

```javascript
many('emma', 'is')
// x: emma
// y: is
// z: []
```

## 用途 2 — 解構賦值 (destructuring)

```javascript
const [a,b] = [1,2];
console.log(a); // 1
console.log(b); // 2
```

```javascript
const [a, ...b] = [1, 2, 3];
console.log(a); // 1
console.log(b); // [2, 3]
```

```javascript
let me = {
  name: 'emma',
  age: 18
};
let { name, age } = me;
console.log(name); // emma
console.log(age);  // 18
```

```javascript
let {a, b, ...rest} = { a:1, b:2, c:3, d:4 };
console.log(a); // 1
console.log(b); // 2
console.log(rest); // {c:3, d:4}
```

```javascript
let [c, ...d] = [1]
console.log(c); // 1
console.log(d); // []
```

---

# 總結與差異

展開運算子的概念可以想成是一種灑進去的感覺，
把陣列或是可迭代的物件展開成一個一個獨立的值，
再灑進使用他的地方。

而其餘運算子則是集合剩下來的值組合成陣列，
讓我們可以傳遞未知數量的參數至函式中
