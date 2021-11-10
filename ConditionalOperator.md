## 語法
```javascript=
condition ? exprIfTrue : exprIfFalse
```

## 參數
```javascript=
condition
值用來做為條件的表達式
```

```javascript=
exprIfTrue
如果 condition 的值是 true , exprIfTrue  會被執行
```
```javascript=
exprIfFalse
如果 condition 的值是 false , exprIfFalse  會被執行
```

## 範例
```javascript=
var age = 26;
var beverage;
if (age >= 21) {
  beverage = "Beer";
} else {
  beverage = "Juice";
}
console.log(beverage); // "Beer"
```

Equivalent to:

```javascript=
var age = 26;
var beverage = (age >= 21) ? "Beer" : "Juice";
console.log(beverage); // "Beer"
```

---

### 條件鏈
```javascript=
function example(…) {
    return condition1 ? value1
         : condition2 ? value2
         : condition3 ? value3
         : value4;
}
```

Equivalent to:

```javascript=
function example(…) {
    if (condition1) { return value1; }
    else if (condition2) { return value2; }
    else if (condition3) { return value3; }
    else { return value4; }
}
```

# [回目錄](./README.md)