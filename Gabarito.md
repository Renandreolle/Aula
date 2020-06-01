# Gabarito

## Exercício 1

~~~Javascript
let arr = ['letra','reduzida','mapeada','grande'];
let mapa = arr.map(texto => texto.toUpperCase());
console.log(mapa); // [ 'LETRA', 'REDUZIDA', 'MAPEADA', 'GRANDE' ]
~~~

## Exercício 2

~~~Javascript
let str = ['1','4','10','7','1','4','4'];
let num = str.map(string => Number(string)).sort((a,b) => a - b);
console.log(num); // [1, 1, 4, 4, 4, 7, 10]
~~~

## Exercício 3

~~~Javascript
let nums = [1, 1, 4, 4, 4, 7, 10];
let prod = nums.reduce((acc,value) => acc * value, 1);
console.log(prod) // 4480
~~~

## Exercício 4

~~~Javascript
let str = ['1','4','10','7','1','4','4'];
let counter = str.reduce((acc,value,index) => {
  if(value === '4') {
    acc.push(index);
    }
  return acc;
  }, []);
console.log(counter); // [1, 5, 6]
~~~

## Exercício 5

~~~Javascript
let str = ['1','4','10','7','1','4','4'];
let obj = str.reduce((list,nums) => {
  list[nums] = list[nums] ? list[nums] + 1 : 1;
  return list;
  }, {});
  console.log(obj); // { '1': 2, '4': 3, '7': 1, '10': 1 }
~~~
