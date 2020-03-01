# Course ECMAScript/JavaScript Foundation I

## Work in progress
este documento ainda não está completo ou revisado!


### Introduction

JavaScript não é mais uma linguagem de “criança”, esse tempo já se foi a muitos anos atrás. Hoje JavaScript é usado por grandes companhias tem aplicações em JavaScript, como Netflix e Paypal.
Com JavaScript você é capaz de construir aplicações inteiras com front, back e DB. Pode construir web apps, mobile apps, real-time apps (chats, streaming), commands line e games.


### Build for browsers but …

JavaScript foi incialmente feito para roda em browsers e cada um deles tem seu “motor” para isso, o Firefox usa “SpiderMonkey” e o chrome usa o “V8”. Porem um engenheiro muito sagaz teve a ideia de “embedar” o V8, que é open source, em um programa c++ criando o Node que roda em back end.


### ECMAScript

ECMAScript define as especificações da linguagem. Começou com o a V1 em 97 e até a V6, em 2015, seguia tal padrão, mas passou a levar o ano a partir de então. O 	que aconteceu foi que a V6 chegou com muita coisa depois de um longo período sem novas versões, gerando um certo caos com a quantidade de novidades e para evitar isso novamente agora todo ano é lançada uma versão com algumas novas features.



### Start with the basic

É importante dizer que em JS cada arquivo é um programa por si só, um arquivo pode falhar ao copilar ou executar, mas isso não impede que os outros arquivos sejam processados. 
Assim sendo, se sua aplicação depende de mais de um arquivo e um deles falha, sua aplicação vai correr, mas vai apresentar falhas, no melhor dos casos.
Para interagir entre si os vários arquivos devem compartilhar o estado pelo “global scope”.
Desde o ES6, JS tem suporte a “module”. “modules” são, também, file-based e quando um “module” é importando em um outro programa, eles são tratados como um.
Em JS para se ter acesso a um modulo você precisa, necessariamente, importa-lo.
Em resumo, é importante tratar cada arquivo como se fosse um programa e ter cuidado com seu funcionamento.


 > Obs: Hoje em dia com os processos de build os projetos unificam todos os arquivos em um só. 
  Assim sendo, eles são tratados como um único programa.
 	
  
	
Values & Variaveis

Variaveis são onde armazenamos valores para serem usados pelo programa
Valor é a fundamental unidade de informação de um programa. São como os programas mantem o “state”. Em JS temos dois tipos de valores: primitive e object.


String
	
String é um valor primitivo usado para representar palavras e frases. Você usa ‘ ou “ para delimitar.

Ex: 
`"Bazinga"` ou `'Bazinga'`

Você pode usar tanto aspas simples, quanto aspas duplas é uma questão de preferência, apenas escolha uma e se mantenha fiel a ela em todo o código.
Strings também podem ser delimitadas com **`**, mas nesse caso não é só uma questão de estilo ou preferência, nesse temos um comportamento diferente.
	
Ex: <br>
  job = 'developer'; <br>
  `console.log(‘I work as ${ job }’)   //  I work as ${ job }` <br>
  `console.log(“I work as ${ job }”)  // I work as ${ job }` <br>
  ``console.log(`I work as ${ job }`)   // I work as developer`` <br>

Temos aqui uma "interpolation" onde o valor dentro de `${ }` é interpretado. Também conhecido como **template literal**


### Number
	
Number representa os valores numéricos do programa tanto inteiros, negativos ou floats

Ex: 
`1, -100, 3.14`


### Boolean

Boolean tem dois valores true e false

### null & undefined

null e undefined são 2 valores primitivos que indicam a falta de valor. Embora os 2 possam ser usados para indicar um valor “vazio” o mais aconselhado é usar undefined ( mais detalhes no final )

### Symbol
Não vamos cobrir, mas existe. São mais low-level code, usado em frameworks e libraries
	

### Arrays and Objects

Além dos primitivos temos Objects

### Array

Array é um tipo especial de Objeto ordenado e indexado
Ex: <br> 
 `code = [ “javascript”, ”html”, “css”]`

Para acessar um valor dentro do array, declara o array e o index desejado

Ex: <br> 
`code[0] = “javascript”`

Como podemos ver no exemplo, o index do array se inicia em 0, então um array de 3 elementos vai ter os index 0, 1, 2 .
Arrays podem guardar qualquer tipo de valor string, number, boolean, outros objetos e ate funções (que ainda vamos cobrir)


### Object

Object guarda as informações em chave/valor. Os valores são acessados chamando as chaves

Ex: 	
  ```
  person = {
    name: “Gustavo”,
      age: 33,
      address: {
        street: “um endereço qualquer”,
        zipCode: 00000
    },
    hobbies: [‘games’, ‘jiu-jitsu’, ‘drink’]
  }

  person.name // Gustavo
  person.hobbies[0] // games
```


### Functions
	
Funções são identificadores que podem ser invocados quantas vezes forem necessárias, pode receber algum valor e podem ou não retornar algum valor. Funções podem ser ‘declaration’ ou ‘expression’

```
function saySomethig() {
	console.log(‘hello to javascript world’);
}
```

Esse é exemplo de ‘function declaration’, nesse caso a associação é feita na fase de compilação, antes do código ser executado.


```
var saySomething = function() {
	console.log(‘hello to javascript world’);
}
```

Esse é um exemplo de ‘function expression’. Diferente da por declaration, por ‘expression’ a associação é feita no ‘runtime’.

É importante perceber que funções são um valor e por isso podem ser assigned e passadas pelo programa. Isso é uma característica importante de um linguagem funcional.

Funções podem receber valores que chamamos de parâmetros

```
function sayMyName(name) {
	console.log(`${name} !!!`);
}

sayMyName(“Gustavo”); // “Gustavo !!!”
```

nesse exemplo chamamos a função passando o valor “Gustavo”, que chamamos de argumento, e dentro do scope da função é representado pelo parâmetro name.

Uma função pode receber n parâmetros, cada parâmetro vai ser designado com o valor do argumento na posição relativa.

```
function sayMyName(firstName, lastName) { ... }
// parametro          0          1
```
```
sayMyName(“Gustavo”, “Pereira”); 
// argumento  0          1
```

e funções podem, também, retornar um valor usando return

```
function sayMyName(name) {
	return `${name} !!!`
}

var msg = function(“Gustavo”);
console.log(msg); // “Gustavo !!!”
```

e como funções são valores, elas podem ser passadas como valores em objetos

```
  var riu = {
      punch() {
        consule.log(‘giving punch!!!’)
    },
      kick() {
        consule.log(‘kicking some ass!!!’)
    },
      haduken() {
        consule.log(‘haDUUUUUUUUUUUken!!!’)
    }
  }

  riu.haduken(); // “haDUUUUUUUUUUUken!!!”
```

esse metodo era muito usando antes de termos class



### Back to variables

Variáveis podem receber qualquer tipo de valor primitivo ou objeto e ser invocado posteriormente. 
As variáveis precisam ser declaradas antes de serem usadas e para isso podemos usar 3 formas e cada uma delas tem um comportamento diferente

#### var
var keyword nos permite declarar uma variável iniciando ou não com algum valor

```
var name = “Gustavo”;
var age;
```


#### let
com let a declaração funciona do mesmo modo

```
let name = “Gustavo”;
let age;
```

Porem let tem acesso mais limitado do que o var, que chamamos de block-scope

```
var name = “fulano”

if (true) {
	let age = 33;	
}

console.log(name) //  fulano
console.log(age) // Error
```
 
Tentar acessar uma variável declarada com if fora do seu bloco vai levar a um erro. Veremos mais sobre scope mais a frente.



#### const
Ao inicializar uma const você deve declarar um valor inicial e esse valor não pode ser redefinido depois

```
const name = “Gustavo”;

if (true) {
  name = “John Wick”; // Error
}
```

Mas const não é 100% imutável 

```
const person = {
	name: “Gustavo”
	age: 33
}

person.job = “JS developer”
person = []; // Error
```

Apesar de a const não poder ser redefinida as propriedades do objeto podem ter seus valores alterados

Por último, em uma função

```
function print(msg) {
	console.log(`the msg is: ${msg}`)
}
```

Dentro do scope da função é criada a variável msg, e ela é acessível somente dentro da função
	



### Values vs References
	
Agora que sabemos variavéis e valores, vamos ver algo fundamental quando se trabalha com eles que é a forma como eles são passados adiante.

Como em qualquer linguaguem um valores podem ser passados como valor ou como referência, porem em JS isso é determinado pelo tipo do valor.

Todos os valores primitivos são passados como copias do valor

```
var myClass = “Cleric”
var yourClass = myClass

myClass = “Warrior”

console.log(myClass) // Warrior
console.log(yourClass  ) // Cleric
```


Alterar um não altera outro, pois são valores distintos.

Já objetos são passados por referência

```
var aragorn = {
  race: “human”,
  class: “warrior”,
  lvl: 1
}
```

os 2 são humanos guerreiros, vou usar o mesmo objeto

```
var boromir = aragorn

aragorn.lvl = 10

console.log(aragorn.lvl) // 10
console.log(boromir.lvl) // 10
```

Como aragorn é um objeto qualquer cópia dele é feita por referência, logo, boromir é uma referência ao mesmo objeto que aragorn. Assim sendo, alterando um você está alterando o outro.

Esse comportamento é imutável dentro do JS.


### Operadores de assignment

```
  // = : define o valor que esta a direita na variável
  x = 10;

  // + : soma de valores
  x = x + 10;

  // - : diminuição de valores
  x = x - 10;

  // * : multiplicação de valores
  x = x * 10;

  // / : divisão de valores
  x = x / 10;

  // % : resto da operação
  x = x % 2;

  x = 15 % 2; // 1, pq 15 dividido por 2 sobra 1
```


Operadores de comparação

###### == Igual, retorna true se os operandos forem iguais 
```
3 == 3      // true
3 == '3'    // true
```

###### != diferente, retorna true se os operandos forem diferentes
```
3 != 4 	              // true
'porto' != 'lisboa'   // true
```

###### === strict igual, retorna true se os operandos forem iguais e do mesmo type
```
3 === 3        // true
'3' === '3'    // true
```

###### !== strict diferente, retorna true se os operandos não forem iguais ou de type diferentes
```
3 !== '3'  // true
```

###### > maior que, retorna true se o valor da esquerda for maior
```
4 > 3  // true
```

###### >= maior que ou igual, se o valor da esquerda for maior ou igual
```
3 >= 3   // true
3 >= 2   // true
```

###### < menor que, retorna true se o valor da esquerda for menor
```
1 < 5   // true
```

###### <= maior que ou igual, se o valor da esquerda for maior ou igual
```
1 <= 1    // true
1 <= 10   // false
```

Nos operadores de igualdade temos 2 tipos de comportamento strict ou não.
De maneira grosseira podemos dizer que o strict equal ele valida valor e tipo do valor
```
3 === 3 // true. value 3 type number 
3 === '3' // false. value 3 type string
```

Na verdade ambos levam o type em consideração, porem == ele, antes de comprar, ele permite que os valores sejam convertidos para o mesmo type.
```
1 == true // true
```

Como estamos comparando um number com um non-number, o  == converte true para number (1) antes de comparar.

Esteja atento que só usar o === não adianta muito, porque `>=` e `<=` funcionam da mesma maneira que o `===`. 
Sendo assim é melhor entender seu funcionamento. Esteja atento que a natureza do `==` é dar preferência a primitivos e números

### Igualde com objetos

```
[1,2,3] === [1,2,3] // false
{a:1} === {a:1}	    // false

var x = [1,2,3];
var y = x;

x === y     // true
x = [1,2,3] // false
```

Aqui estamos querendo comprar a estrutura do objeto, mas para objetos o === trabalha de forma diferente, como vimos, objetos são passados por referência. Nesse exemplo quando comparamos x e y é true porque ambos apontam para a mesma referência, já x = = = [1,2,3] está comparando x a uma nova referência. A estrutura e valores nela contidos não são levados em conta pelo JS, somente sua referência. 
	

### Operador ternário

É o único operador que leva 3 parâmetros

`Condição ? valor1 : valor2` <br>

Se a condição for verdadeira o operador terá valor1, caso contrario valor2

`var status = (age >= 18) ? 'adult' : 'minor'`

### Operadores unitarios

- delete
- in
- Typeof

[ WIP ]



