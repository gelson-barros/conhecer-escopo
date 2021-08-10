# **Escope**

Existe três tipos de escopos que são:

* Escopo funcões 
* Escopo blocos
* Escopo léxico

**O que é o escopo?**

O escopo pode ser a visibilidade de uma variável.

**Como assim?**

Depedendo de como você declara uma variável outras partes dos seu codigo podem ou não acessar esta variável.


## **Escopo da Funcão**
```javascript

functiom getMessage(){
    let message = 'Oi';
    message // 'Oi!'
}
message // not defined(não foi definida)

```

__"message"__ é acessivel apenas dentro da função getMessage

```javascript

function myFunc(){
    let cat = 'Bebucho';
    const age = 3;
    var color = 'cinza'

}
myFunc();
cat // not defined
age // not defined
color // not defined

function myFunc2(){
    
    const age = 5;
    var color = 'branco' 

}
```

__"cat, age, color"__ é acessivel apenas dentro da função myFunc

*As variáveis dentro da funcao não exitem fora da função, isto significa que que pode se ter multiplas funções que tem variaveis e constantes com os mesmo nomes dentro delas*

````javascript
//Exemplo1
const dog = "Pastor-Alemão"

function dogWatch(){
    const dog = "Samoieda"
    dog // Samoieda
}
dog//Pastor-Alemão


//Exemplo2
const great = "oi"
const great = "olá"//erro: a great já foi declarada

````

*No exemplo1 acima muda par let ou var a declaração de variavel vai ter o mesmo comportamento*

*No exemplo2 const e let tem o mesmo comportamento e o var aceita*

## **Escopo de Blocos**

*Um bloco tem a notação de abertura e fechamento de chave{ }. Então for, while, do-while, for-in for-of, e todos que tem chavetar na suas estruras.*

````javascript 
let radius = 8;
if(radius> 0 ){
    const PI = 3.14
    let circle = 2 * PI * radius
}

radius // 8
PI // not defined
circle// not defined

true
if(){
    var dragon = "Balerion"
    dragon // Balerion
}

dragon // Balerion
````
*No escopo de bloco só as let e const cumprem*

## **Escopo Léxico**

*Funções aninhadas estarem sugeitas a buscar variaveis que não tem no seu escopo ir no escopo acima delas, somente tem um fluxo(dentro para fora)*

````javascript
const external = () => {
    const greet = "oi";

    const internal = ()=>{
        //const greet = "Ola";
        const message = `${greet}. Seu pai tem boi?`;
        console.log(message);
    }

    internal();
}
//a variavel greet o seu valor é visivel na funcao internal
````

````javascript
const external = () => {
    const book = 'Sapiens';

    const internal = () => {
        //const book = 'Os testamentos';

        const extraInternal = () => {
            console.log(book.toUpperCase());
        }
        
        extraIternal();
    }
    internal();
}

````