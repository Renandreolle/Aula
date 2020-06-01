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
---
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
---

A função *Array.reduce* é diferente das outras HOFs, pois além na função que é passada como parâmetro, além do valor iterado passado como parâmetro é também passada uma variável denominada **acumulador**, que serve para armazenar os resultados das iterações e é também o que a função *reduce* retorna. Após a função passada como parâmetro, podemos também passamos o valor inicial do acumulador.

Por exemplo, se temos um array de números e quisermos somar esses números, podemos usar o acumulador para guardar o resultado das somas com os valores em cada iteração.
Para ficar mais claro, observe esse exemplo:

~~~Javascript
let array = [2, 4, 6, 8];
let somatorio = array.reduce((somaParcial, valor) => valor + somaParcial, 0); // Passamos o valor inicial do somaParcial como 0.
console.log(somatorio); // 20, que é a soma dos números do array.
~~~

<br>
Podemos ver nessa tabela o fluxo de iteração:

Iteração | Acumulador antes | valor | Acumulador depois
---------|------------------|-------|------------------
1 | 0 | 2 | 2
2 | 2 | 4 | 6
3 | 6 | 6 | 12
4 | 12 | 8 | 20

<br>
Note que nas outras HOFs, nossa função passada como parâmetro recebia apenas os valores do array, mas no caso do *reduce*, essa função recebe também o acumulador, que no exemplo passado, era a soma parcial do somatório.
Além do valor e do acumulador, a função auxiliar pode ter outros 2 parâmetros opcionais, de forma que nosso reduce pode ser escrito assim:
`esseArray.reduce((acumulador,valor,index,array) => { 'seu código aqui' }, valorInicial)`
Onde o index se refere ao índice do valor iterado, e array se refere ao próprio array iterado (esseArray). Lembre-se que **a ordem é importante aqui**: O acumulador é declarado primeiro, depois o valor, o índice e o array. Usaremos esses parâmetros opcionais no próximo exemplo:

<br>
~~~Javascript
const nums = [1,2,3,4,5,6,'ignora']
const totalNumero = nums.reduce((soma,valor,indice,array ) => {
    if(indice < array.length-1) { // Queremos ignorar o último item por não ser um número
        soma += valor;
    }
    return soma; // Se não colocar return, a função retorna undefined
}, 0);
console.log(totalNumero); // 21, que é a soma dos números do array nums
~~~

<br>
Esses parâmetros adicionais nos permitem fazer operações sem ter que usar explicitamente variáveis definidas fora do escopo, tornando nosso código conciso e legível.
Note que o valor do acumulador pode ser uma string, array ou objeto. Nesse outro exemplo, vamos criar um objeto:

<br>
~~~Javascript
const arr = ['um','dois','três','quatro'];
const obj = arr.reduce((lista,numero,indice) => { // Note que usaremos o parâmetro opcional indice
        lista[numero] = indice + 1; // Aqui colocamos como chave do acumulador o numero e o valor associado é o índice + 1
        return lista; // Nosso acumulador
    }, {} // O valor inicial do acumulador foi um objeto vazio
    );
console.log(obj); // { um: 1, dois: 2, 'três': 3, quatro: 4 }
~~~
<br>


## Vamos fazer juntos!

É hora de colocar em prática todo esse conhecimento. 💪

Aula ao vivo! Vamos para o Slack, onde o link estará disponível.

<br>
## Exercícios

Hora de pôr a mão na massa!
<br>

### Antes de começar, versionando o seu código

Para versionar seu código, utilize o seu repositório do GitHub pages. 😉

Abaixo você vai ver exemplos de como organizar cada exercício em uma branch, com arquivos e commits específicos para cada exercício. Você deve seguir este padrão para realizar os exercícios a seguir.
<br>

1. Crie uma branch com o nome exercises/9.2 (bloco 9, dia 2)

~~~bash
$ git checkout -b exercises/9.2
~~~
<br>


2. Crie um diretório exercises e, dentro dele, um diretório 9_2. O caminho completo para o diretório a partir da raiz do projeto deverá ser exercises/9_2.

~~~bash
$ mkdir -p exercises/9_2
$ cd exercises/9_2
$ pwd
<path_to_your_github_pages_repo>/exercises/9_2
~~~
<br>

3. Crie um arquivo com um nome descritivo para cada exercício. Os arquivos devem estar dentro da pasta exercises/9_2, mas lembre-se de fazer os commits a partir da pasta raiz do seu projeto!

~~~bash
$ git status
On branch exercises/9.2
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

  modified:   exercise_1.html
~~~
<br>

4. Faça commits organizados durante o processo de resolução de cada um de seus exercícios. As mensagens dos commits devem ser breves e explicativas.

~~~bash
 git log
commit 100c5ca0d64e2b8649f48edf3be13588a77b8fa4 (HEAD -> exercises/9.2)
Author: Tryber Bot <tryberbot@betrybe.com>
Date:   Fry Sep 27 17:48:01 2019 -0300

    Exercicio 2 - mudando o evento de click para mouseover, tirei o alert e coloquei pra quando clicar aparecer uma imagem do lado direito da tela

commit c0701d91274c2ac8a29b9a7fbe4302accacf3c78
Author: Tryber Bot <tryberbot@betrybe.com>
Date:   Fry Sep 27 16:47:21 2019 -0300

    Exercicio 2 - adicionando um alert, usando função e o evento click

commit 6835287c44e9ac9cdd459003a7a6b1b1a7700157
Author: Tryber Bot <tryberbot@betrybe.com>
Date:   Fry Sep 27 15:46:32 2019 -0300

    Resolvendo o exercício 1 usando eventListener
~~~
<br>

5. Lembre-se que na primeira vez que você for enviar o código para o repositório remoto a branch exercises/9.2 não vai existir lá.
Então você precisa configurar o remote utilizando a opção --set-upstream (ou -u, que é a forma abreviada).

~~~bash
 git push -u origin exercises/9.2
~~~
<br>
 
 6. Lembre-se de enviar os commits para o repositório do GitHub de vez em sempre.
 
 ~~~bash
  git push origin exercises/9.2
~~~
 <br>
 
 7. Quando terminar os exercícios, seus códigos devem estar todos commitados na branch exercises/9.2, e disponíveis no repositório remoto do GitHub.
Pra finalizar, crie um [Pull Request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) , adicione uma descrição bem bacana, e envie para a monitoria e/ou colegas revisarem! 🤜🏼🤛🏼
<br>

### Agora a prática

<br>

## Recursos adicionais

* [Página da w3schools sobre map](https://www.w3schools.com/jsref/jsref_map.asp)
* [Página da w3schools sobre reduce](https://www.w3schools.com/jsref/jsref_reduce.asp)
* 

