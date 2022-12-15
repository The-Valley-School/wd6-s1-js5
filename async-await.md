Con async y await tenemos un modo ‘más limpio’ para trabajar con promesas.

El uso de async en la declaración de una función la convierte en una promesa la cual se resuelve mediante un retorno. 

Dentro de estas funciones podemos usar await, con el objetivo de parar la ejecución hasta que se resuelva la promesa. Se reanudará una vez cumplida.


```jsx

/* Opción 1 */
function getUsers (){
	const URL = "https://reqres.in/api/users?page=2";
	
	fetch(URL)
	.then(respuesta => respuesta.json())
	.then(respuesta => console.log(respuesta.data))
	.catch(error => console.log(error))
}

/* Opción 2 */
getUsers();
async function getUsers(){
    const URL = "https://reqres.in/api/users?page=2";
    const response = await fetch(URL);
    const datosFormateados = await response.json();
    return datosFormateados;
}

getUsers().then(respuesta => console.log(respuesta))
```