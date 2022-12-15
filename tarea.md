Llega el turno de la práctica, hoy vamos a hacer este programita que cuando introduces un nombre te pinta la edad que devuelve un servicio al que llamamos.

La documentación del servicio get está en la página:

https://agify.io/


![tarea](recursos/Untitled%203.png)

- Funcionalidad
    - Llamar al servicio con el nombre introducido y mostrar la edad
    - En caso de que no devuelva edad mostrar por pantalla un guión y por consola que se ha producido un error

- Diseño
    - Font family → monospace
    - Fondo: `background: linear-gradient(to right, #24243e, #302b63, #0f0c29);`
    - Sombra del texto: `text-shadow: 6px 6px 0px rgba(0,0,0,0.2);`
    - Sombra de los divs: `rgba(50, 50, 93, 0.25) 0px 50px 100px -20px, rgba(0, 0, 0, 0.3) 0px 30px 60px -30px;`
    - Colores:
        - color botón adivinar: #8c8a4a;
        - hover adivinar: #414022;
        
- Algunos tamaños (No es necesario ir al píxel)
    - El contenedor general tiene un tamaño máximo de 500px y un padding de 10px
    - La letra del título son 50px
    - La letra del input 18px y del número 100px