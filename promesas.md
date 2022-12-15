En este video vamos a ver lo que son las promesas y como podemos trabajar de una manera adecuada con ellas para poder trabajar mejor la asincronía.

Como dato, antes de las promesas, solo teníamos los callbacks que hemos visto para poder trabajar la asincronía.

¿Qué entendemos de un objeto promise? Básicamente es la representación de una tarea que en algún momento del futuro debería proporcionar un resultado que será consumido (puede que no se cumpla)


### Creando una Promise

La estructura es la siguiente 


```jsx
const miPrimeraPromesa = new Promise(function(resolve, reject) {
  // tarea a realizar
});
```


La función que se pasa como argumento es la función ejecutora, recibe 2 argumentos y se llamará nada más crearse el objeto.

- resolve → función a la que invocamos para decirle a JS que la tarea se ha solucionado sin incidencias.
- reject → función que se invoca en caso de que suceda un error con la tarea.

Vamos a ver un ejemplo:


```jsx
const promise = new Promise (function (resolve, reject) {
	setTimeout(function (){
		console.log("Mensaje Timeout");
		resolve("devuelvo el valor");
	}, 1000);
});
```


Ahora veremos la forma de recuperar ese valor  del resolve con los métodos then y catch pero primero tenemos que recalcar que estas promesas tienen 3 estados:

- “pending” mientras la tarea se completa.
- “fullfilled*”,* si la tarea se completó con éxito (invocando `resolve` )
- “rejected” en el caso de que se produjese un error (invocando `reject` )


### Consumiendo una Promise

Ahora que ya sabemos crearlas, tenemos que ver como acceder al valor que devuelven 


**THEN**

El método then recibe 2 argumentos:

- Una función que recibe como argumento el valor devuelto por la promise en caso de que se resuelva con **resolve**
- Una función que recibe como argumento el error en caso de que se haya entrado en juego el **reject**

 
```jsx
const promise = new Promise (function (resolve, reject) {
	setTimeout(function (){
		console.log("Mensaje Timeout");
		resolve("devuelvo el valor");
	}, 1000);
});

promise.then(
	function(result){ console.log(result) }, 
	function(error){ /* hacemos algo con el error */}
);
```


**CATCH**

Es cierto que podemos usar el segundo argumento para capturar los errores pero por lo general usamos el método catch.


```jsx
const promise = new Promise (function (resolve, reject) {
	setTimeout(function (){
		console.log("Mensaje Timeout");
		reject(new Error('ha fallado'));
	}, 1000);
});

promise.catch(
	function(error){ console.log(error.message)}
)
```


**FINALLY**

Tenemos la opción de ejecutar un trozo de código independientemente del resultado de la promesa.


```jsx
const promise = new Promise (function (resolve, reject) {
	setTimeout(function (){
		console.log("Mensaje Timeout");
		reject(new Error('ha fallado'));
	}, 1000);
});

promise
	.catch(function(error){ console.log(error.message)})
	.finally(function(){console.log('me ejecuto siempre')})
```


Hacemos otro ejemplo

```jsx
let listaPartipantes = ['Edu', 'Gon', 'Fran'];

function anadirParticipante (nuevoParticipante, lista){
    const miPromesa = new Promise((resolve, reject) => {
     
        setTimeout(function(){
            if(!lista){
                reject(new Error('No hay lista de participantes'));
            } else {
                lista.push(nuevoParticipante);
                resolve(lista);
            }
        },2000);
    })

    return miPromesa;
}

anadirParticipante('Luis', listaPartipantes)
    .then( function(resultado){ console.log(resultado)})
    .catch( function(error){ console.log(error.message)})
```


### Anidación de promesas

Podemos anidar promesas si queremos que se ejecuten una detrás de otra.

```
anadirParticipante('Luis', listaPartipantes)
    .then( resultado => anadirParticipante('Pedro', listaPartipantes))
    .then( resultado => anadirParticipante('Juan', listaPartipantes))
    .then( resultado => anadirParticipante('Fermín', listaPartipantes))
    .then( resultado => console.log(resultado.join(',')))
    .catch( error => console.log(error.message))
```


### Promise all

¿Qué pasa si tengo que resolver varias promesas a la vez? Tenemos que utilizar el promise all


```jsx
let p1 = new Promise((resolve, reject) => {
  setTimeout(resolve, 1000, "one");
});
let p2 = new Promise((resolve, reject) => {
  setTimeout(resolve, 2000, "two");
});
let p3 = new Promise((resolve, reject) => {
  setTimeout(resolve, 3000, "three");
});
let p4 = new Promise((resolve, reject) => {
  setTimeout(resolve, 4000, "four");
});
let p5 = new Promise((resolve, reject) => {
  reject("reject");
});

Promise.all([p1, p2, p3, p4, p5]).then(values => {
  console.log(values);
}).catch(reason => {
  console.log(reason)
});

```