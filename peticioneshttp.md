### Peticiones HTTP

LLegamos a una parte guay, que son las peticiones HTTP. 

Hasta ahora, habíamos trabajado siempre con información que teníamos en variables, después de este video sabremos tratar información que venga de un servidor web.

Una petición HTTP es la acción por parte del navegador para solicitar un recurso (documento, archivo, fichero html…) a un servidor. Esa información la recibe el navegador y nosotros la podemos tratar.

Recordad esta foto que vimos en el prework:

![http](recursos/Untitled%202.png)

Las peticiones que nos interesan ahora a nosotros son las peticiones AJAX, que son las peticiones HTTP que se realizan desde Javascript y que podemos tratar antes de que se muestren por pantalla. 

Existen 2 formas nativas de hacer estas peticiones desde JS:

- XMLHttpRequest
- fetch


### Fetch

Vamos a ver como hacer peticiones con fetch que es el sistema más moderno. Fetch nos permite el acceso a rescurso del servidor de forma asíncrona, si necesidad de recargar la página.

Tenemos que entender también que fetch tiene la estructura de una promesa utilizando el then y el catch.


```jsx
fetch(URL)
.then(res => res.json())
.then(res => console.log(res));
.catch( err => console.error(err));
```

### Tipos de peticiones fetch

- GET → Petición que se utiliza para obtener datos
- POST → Para enviar datos, como nuevos registros
- PUT → Para actualizar información existente
- DELETE → Para eliminar información existente

 

Vamos a hacer pruebas con los servicios que nos proporciona esta web:

[https://reqres.in/](https://reqres.in/)

**Petición GET**:


```jsx
const URL = "https://reqres.in/api/users?page=2";

fetch(URL)
.then(respuesta => respuesta.json())
.then(respuesta => console.log(respuesta.data))
.catch(error => console.log(error))
```


**Petición POST**


```jsx
const URL = "https://reqres.in/api/users";

fetch(URL, {
    method: 'POST',
    headers: {
        "Content-Type": "application/json",
    },
    body: JSON.stringify({ name: 'Eduardo', job: 'Profesor' })
})
.then(respuesta => respuesta.json())
.then(respuesta => console.log(respuesta))
.catch(error => console.log(error))
fetch(URL, {
    method: 'POST',
    headers: {
        "Content-Type": "application/json",
    },
    body: JSON.stringify({ name: 'Eduardo', job: 'Profesor' })
})
.then(respuesta => respuesta.json())
.then(respuesta => console.log(respuesta))
.catch(error => console.log(error))
```


**Petición PUT**


```jsx
const URL = "https://reqres.in/api/users";

fetch(URL, {
    method: 'PUT',
    headers: {
        "Content-Type": "application/json",
    },
    body: JSON.stringify({ name: 'Eduardo', job: 'Albañil' })
})
.then(respuesta => respuesta.json())
.then(respuesta => console.log(respuesta))
.catch(error => console.log(error))
fetch(URL, {
    method: 'POST',
    headers: {
        "Content-Type": "application/json",
    },
    body: JSON.stringify({ name: 'Eduardo', job: 'Profesor' })
})
.then(respuesta => respuesta.json())
.then(respuesta => console.log(respuesta))
.catch(error => console.log(error))
```


**Petición DELETE**


```jsx
const URL = "https://reqres.in/api/users/2";

fetch(URL, { method: 'DELETE' })
.then(() => console.log('delete correcto'))
.catch(error => console.log(error))
```
