# Javascript ES6 - Higher Order functions - map e reduce 

## O que vamos aprender?

Hoje vamos aprender sobre as funções _Array.map_ e _Array.reduce_. Como vimos na aula passada, elas atuam em um array e recebem uma função como parâmetro, assim como as outras higher order functions. Elas são funções bastante poderosas, que acompanharão vocês ao longo da jornada de programação.

### Você será capaz de:

* Utilizar a função *Array.map* para iterar construir novos arrays
* Utilizar a função *Array.reduce* para manipular os valores dos arrays de formas diversas


## Porque isso é importante?

As funções da aula de hoje possuem uma importância adicional, seja pelo poder e concisão que trazem ao código, seja pela alta utilização.

## Conteúdos
##### Tempo sugerido para realização: 90 minutos

### Array.map
A função *Array.map* é bastante similar à função *Array.forEach*, porém com uma diferença importante: a função *map* retorna um novo array com o mesmo tamanho do array original, já *forEach* retorna sempre undefined, o que nos forçava a criar uma variável adicional para armazenar os valores durante a iteração, como podemos ver no código abaixo:

~~~Javascript
let a = [1, 2, 3];
let b = []; // Necessário para guardarmos os valores com forEach

a.forEach(numero => b.push(numero**2));

let c = a.map(numero => numero**2);

console.log(a); // Permanece inalterado como [1, 2, 3]
console.log(b); // [1, 4, 9]
console.log(c); //[1, 4, 9]
~~~

Dado que *map* nos retorna um array, podemos aproveitar disso para encadear uma outra HOF, como veremos na comparação de baixo usando as funções *forEach* e *map*, que vão pegar um array de números, elevá-los ao quadrado e depois filtrar os números ímpares. Com a função *forEach*, temos:

~~~Javascript
let a = [1, 2, 3];
let b = [];
a.forEach(numero => b.push(numero**2));
b = b.filter(numero => numero%2 === 1);
console.log(b); // [1,9]
~~~

Já utilizando a função *map*, temos:

~~~Javascript
let a = [1, 2, 3];
let c = a.map(numero => numero**2).filter(numero => numero%2 === 1);
console.log(c); // [1,9]
~~~

Como podemos ver, *map* nos permite escrever iterações sobre arrays de forma extremamente enxuta, se comparado ao mesmo código usando *forEach* ou *for*.

### Array.reduce

A função Array.reduce é diferente das outras HOFs, pois além na função que é passada como parâmetro, além do valor iterado passado como parâmetro é também passada uma variável denominada **acumulador**, que serve para armazenar os resultados das iterações e é também o que a função *reduce* retorna. Após a função passada como parâmetro, podemos também passamos o valor inicial do acumulador.
Para ficar mais claro, observe esse exemplo:

~~~Javascript
let array = [1, 2, 3];
let somatorio = array.reduce((somaParcial, valor) => valor + somaParcial, 0); // Passamos o valor inicial do somaParcial como 0.
console.log(somatorio); // 6, que é a soma dos números do array.
~~~

Note que nas outras HOFs, nossa função passada como parâmetro recebia apenas os valores do array, mas no caso do reduce, essa função recebe também o acumulador, que no exemplo passado, era a soma parcial do somatório. 

## Vamos fazer juntos!
## Exercícios
## Recursos adicionais
> Aula sim
