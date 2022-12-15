No somos perfectos y en muchas ocasiones nuestro código va a tener errores y respuestas inesperadas. Por lo general cuando se produce un error se imprime por pantalla y se bloquea el código. 

Para poder mitigar estos errores y controlar ciertos flujos, tenemos la construcción sintáctica try-catch


### try - catch

La sintaxis es muy sencilla.
 

```jsx
try {
  // Código que queremos ejecutar
} catch (err) {
  // Código que se ejecuta cuando se produce un error en el try
}
```
  

```jsx
try{
    console.log('Hola');
    console.log(a); // error porque la variable a no se ha declarado
} catch{
    console.log('No se ha podido ejecutar');
}

// muestra por consola:
//Hola
//No se ha podido ejecutar
```


Cuando se produce un error se genera un objeto que contiene información detallada:

- nombre: Nombre del error
- message: Mensaje de error
- stack: Mensaje a modo log de la ejecución y el error.

El try…catch se utiliza sobre todo para gestionar JSON.

Imaginaros que el cliente de una web de ropa accede a la sección camisetas. A nivel de código se hace una petición para recibir toda esa información pero el servidor devuelve una estructura errónea. Al cliente no le va a valer con un error mostrado por consola, no? Tendremos que estructurar bien nuestro código y usar el try…catch para dar una solución más satisfactoria.


```jsx
//let json = '{"user":"Edu", "edad": 31}'
let json = "{ #@#¢∞  √¥ }";

// Probamos a parsear nuestro JSON
try {
  let cliente = JSON.parse(json); 
  console.log( cliente.user ); 

} catch (err) {
  // mostraríamos por pantalla un mensaje maquetado.
	console.log("Lo sentimos, no hemos podido cargar los datos, inténtelo de nuevo más tarde")
}
```
 

### throw

En caso de querer unifiar errores (ya que algunos pueden ser cosa nuestra) podemos utilizar el operador throw para lanzar nuestros propios errores. Imaginad que queremos controlar el que no haya user


```jsx
let json = '{"edad": 31}'

// Probamos a parsear nuestro JSON
try {
  let cliente = JSON.parse(json); 
	if(!cliente.user){
		throw new Error("Datos incompletos"); //SyntaxError, ReferenceError...
	}	

} catch (err) {
  // mostraríamos por pantalla un mensaje maquetado.
	console.log("Lo sentimos, no hemos podido cargar los datos, inténtelo de nuevo más tarde")
}
```
 

### finally

El try…catch puede tener una cláusula finally que se ejecuta siempre (después de try si no hubo errores y después del catch si los hubo.

```jsx
try {
  // Código que queremos ejecutar
} catch (err) {
  // Código que se ejecuta cuando se produce un error en el try
} finally {
	// Código que ejecutamos siempre
}
```