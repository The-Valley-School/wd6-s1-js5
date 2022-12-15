¿Qué es una función callback?

Una función callback es una función que se pasa a otra función como si fuese un argumento, pudiéndose invocar dentro de la función ‘padre’ para poder completar algún tipo de acción

Por ejemplo, la función que utilizamos en el video de asincronía:


```jsx
console.log('mensaje 1');

setTimeout(function () {
    console.log('mensaje 2');
}, 300);

console.log('mensaje 3');
```
 

Un ejemplo más visual sería:


```jsx
function saludar(nombre) {
  console.log('Hola ' + nombre);
}

function procesarEntradaUsuario(callback) {
  let nombre = "Edu";
  callback(nombre);
}

procesarEntradaUsuario(saludar);
```


Como hemos comentado con anterioridad, cuando trabajamos con datos de fuentes externas como pueden ser APIs, no tenemos claro cuando nuestros datos van a ser devueltos, por eso necesitamos este tipo de apoyos que resultan muy útiles.

Veamos un ejemplo que simula una solicitud a un servidor.


```jsx
function solicitudServidor(consulta, callback){
  setTimeout(function(){
    let respuesta = consulta + "netflix, hbo, amazon prime";
    callback(respuesta);
  },2000);
}

function obtenerResultados(resultados){
  console.log("## Respuesta del servidor ##");
	consoel.log(resultados);
}

solicitudServidor("Servicios contratados por el usuario: ", obtenerResultados);
```