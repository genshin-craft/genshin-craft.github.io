See GUI Example Page  [Kor](https://genshin-craft.github.io/index.html) / [Eng](https://genshin-craft.github.io/index_en.html)

See Post in [Gamedot](https://genshin.gamedot.org/?mid=board&target=view&board=tip&page=1&post=470)

### Mechanism

First, calculate the items in the same class
Afterwards, each 11 crafting procedure is performed and the final value is returned.

우선 같은 등급에서 재화를 계산합니다.
이후 총 11번의 합성 절차를 거친 후 값을 리턴합니다.
|procedure|Before|After|
|------|---|---|
|5star <-- 4star|0,3,0,0|1,0,0,0|
|4star <-- 3star|0,0,3,0|0,1,0,0|
|5star <-- 3star|0,0,9,0|1,0,0,0|
|3star <-- 2star|0,0,0,3|0,0,1,0|
|4star <-- 2star|0,0,0,9|0,1,0,0|
|5star <-- 2star|0,0,0,27|1,0,0,0|
|5star <-- 3star + 4star|0,2,3,0|1,0,0,0|
|5star <-- 2star + 3star|0,0,8,3|1,0,0,0|
|5star <-- 2star + 4star|0,2,0,9|1,0,0,0|
|4star <-- 2star + 3star|0,0,2,3|0,1,0,0|
|5star <-- 2star + 3star + 4star|0,2,2,3|1,0,0,0|


### Usage

You can download file via this repo, or use script tag like below

파일 직접 받아서 가져와도 되고, script 태그로 가져와 쓰셔도 됩니다.
```
<script src='https://genshin-craft.github.io/craftify_min.js'></script>
```

You can use only 1 function. Make sure the arrays are correctly aligned starting from 5star to 2star.
If the number of item's class is not 4 but 3, you can put 0 value in 5star.

함수는 아래 하나만 쓰시면 됩니다. 배열은 5성에서 2성 순으로 만드시면 됩니다.
만일 아이템 등급이 총 3개라면 5성 부분에 0을 넣으시면 됩니다.
```
const result = craftify ( [possess arr], [target arr] );
```

return value may like below

리턴값은 아래와 같이 나옵니다
```
count : [5star up, 4star up, 3star up],
remain : [remained arr] ,
required : [required arr]
requiredTotal : required item totals
```

Example
```
const result = craftify ([0, 0, 1, 112], [6, 9, 0, 0]);
console.log(result.count); // 1,12,36
console.log(result.remain); // 0,0,1,4
console.log(result.required); // 5,0,0,0
console.log(result.requiredTotal); // 128
```
```
const result = craftify ([6, 0, 11, 0], [6, 9, 9, 1]);
console.log(result.count); // 0,0,0
console.log(result.remain); // 0,0,2,0
console.log(result.required); // 0,9,0,1
console.log(result.requiredTotal); // 76
```
