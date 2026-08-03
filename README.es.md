<!-- hide -->
<div align="center">

# Tutorial API con Node

<img width="560" alt="Portada del tutorial sobre fondo crema: el texto Learn Node EXPRESS Interactive en letras grises grandes, junto a un icono de mano blanca pulsando un botón rodeado de ondas moradas, y la dirección www.4geeks.com sobre una franja negra en la parte inferior" src="https://raw.githubusercontent.com/4GeeksAcademy/node-express-api-tutorial/master/.learn/assets/preview.png">

[![Tutorial interactivo](https://img.shields.io/badge/4Geeks_Academy-Tutorial_interactivo-2563eb)](https://4geeks.com/es/learnpack)
[![Hecho con LearnPack](https://img.shields.io/badge/LearnPack-11_pasos_guiados-2563eb)](https://github.com/learnpack/learnpack)
[![Abrir en GitHub Codespaces](https://img.shields.io/badge/Abrir_en-GitHub_Codespaces-fb5a1f)](https://codespaces.new/?repo=4GeeksAcademy/node-express-api-tutorial)

Lee estas instrucciones en [🇺🇸 inglés](https://github.com/4GeeksAcademy/node-express-api-tutorial/blob/HEAD/README.md)

</div>
<!-- endhide -->

Este tutorial de LearnPack construye una API REST con Node.js y Express en 11 pasos guiados. Terminas con un `app.js` de unas 30 líneas que expone `GET /todos`, `POST /todos` y `DELETE /todos/:todoPosition` sobre un array en memoria, escuchando en el puerto 8080. La dificultad es fácil, la duración estimada es de 8 horas, no hay tests automáticos y cada paso viene en español y en inglés.

<!-- hide -->
## 📋 Sobre este tutorial

- **Dificultad:** fácil. Empieza antes incluso de instalar Express, así que no se da por supuesta ninguna experiencia previa en backend.
- **Duración estimada:** 8 horas.
- **Tecnologías:** JavaScript, Node.js, Express 4.18, línea de comandos y APIs REST.
- **Pasos:** 11 carpetas dentro de `.learn/exercises/`, numeradas del `00` al `08.1`.
- **Corrección:** ninguna. El paquete no incluye ningún fichero de test, así que nada se corrige de forma automática.
- **Soluciones de referencia:** 5 de los 11 pasos incluyen un `solution.hide.js` que puedes destapar.
- **Vídeos de solución:** no hay. En `learn.json`, `videoSolutions` está en `false`.
- **Idiomas:** cada paso trae `README.md` y `README.es.md`.
<!-- endhide -->

## 🎯 ¿Qué vas a aprender?

El tutorial enseña la mitad de atrás de una aplicación web, una idea por paso:

- **Node.js desde la terminal:** comprobar la versión con `node -v`, instalar un paquete con `npm install express --save-dev` y arrancar tu programa con `npm run start`.
- **Qué es Express realmente:** el framework que cargas con `require('express')` y que instancias con `express()` para obtener el objeto `app` del que cuelga todo lo demás.
- **Levantar un servidor HTTP:** `app.listen(8080, callback)` y cómo recuperar el puerto desde `server.address().port` para escribirlo en consola.
- **Rutas:** `app.get()`, `app.post()` y `app.delete()`, y la firma `(req, res)` que comparten todos los manejadores.
- **Responder con texto o responder con JSON:** `res.send('Hello World!')` para una cadena suelta y `res.status(200).json(todos)` para el JSON que se espera de una API REST.
- **Leer el cuerpo de la petición:** por qué hay que registrar `app.use(express.json())` y cómo llega el objeto ya parseado a `req.body`.
- **Leer parámetros de la URL:** declarar `:todoPosition` en la ruta y recogerlo en `req.params.todoPosition`.
- **Guardar el estado en memoria:** un array de JavaScript al que añades con `.push()` y que reconstruyes con `.filter()` para borrar.
- **Probar una API sin frontend:** lanzar peticiones con Postman, Insomnia o cualquier otro constructor de peticiones, porque desde la barra de direcciones del navegador solo se puede enviar un `GET`.

## 👀 ¿Qué vas a construir?

Una única API REST de tareas pendientes con tres endpoints:

```txt
GET    /todos
POST   /todos
DELETE /todos/<posicion>
```

Escribes todo en un solo fichero `app.js` en la raíz del proyecto, y cada paso añade unas pocas líneas a las anteriores. Estas son las 11 carpetas:

1. **`00` Bienvenida:** la especificación que vas a implementar, con la forma exacta de una tarea, `{ "done": true, "label": "Sample Todo 1" }`, y lo que debe devolver cada uno de los tres endpoints.

2. **`01` Instalando Node:** divide la terminal, ejecuta `node -v` e instala Node.js desde nodejs.org si no aparece ninguna versión.

3. **`02` Instalando Express:** `npm install express --save-dev`. El tutorial usa `--save-dev` para que Express quede registrado entre las dependencias del proyecto.

4. **`03` Primera app de Express:** crea `app.js` en la raíz del proyecto con las cuatro piezas que necesita todo lo demás: el `require`, la llamada a `express()`, `app.use(express.json())` y `app.listen(8080, ...)`.

5. **`04` Ejecuta tu app:** `npm run start`, un script que ya está definido en `package.json` para lanzar `node app.js`.

6. **`05` Tu primera ruta:** añade `app.get('/', (req, res) => { res.send('Hello World!') })` y abre el puerto 8080 para ver la cadena en el navegador.

7. **`06` Devolviendo JSON:** declara un array global `todos` que contenga al menos `{ "label": "Drink some water", "done": false }` y añade el `GET /todos` que responde con `res.status(200).json(todos)`.

8. **`07` Post Todo:** tu primer endpoint escrito desde cero. Un `POST /todos` que toma la tarea del cuerpo de la petición, la añade a la lista y devuelve la lista actualizada. El paso te da un ejemplo de `POST /signup` en el que fijarte.

9. **`07.1` Comprobar el post:** la implementación de referencia, construida sobre `req.body`, `todos.push(todo)` y `res.status(200).json(todos)`, además de la petición exacta que debes lanzar desde Postman con el cuerpo `{ "done": true, "label": "Start node API tutorial" }`.

10. **`08` Delete Todo:** el segundo endpoint que escribes tú. Un `DELETE /todos/:todoPosition` que lee la posición desde la URL y elimina ese elemento de la lista.

11. **`08.1` Comprobar el delete:** la implementación de referencia, que reasigna `todos = todos.filter((value, position) => position != todoPosition)` y devuelve la lista ya recortada.

## 🎓 ¿Qué necesitas antes de empezar?

- **JavaScript básico:** declarar variables, arrays de objetos y funciones flecha. Aquí se explica Express, no el lenguaje.
- **Perderle el miedo a la terminal:** los pasos del `01` al `04` son comandos, y el servidor se queda ocupando la terminal mientras trabajas.
- **Nada instalado, si usas Codespaces:** el contenedor parte de la imagen `javascript-node:22` e instala la CLI de LearnPack y su plugin de Node al crearse.
- **Node.js, si trabajas en local:** cualquier versión moderna. El paso `01` muestra `v.16.14.0` como salida de ejemplo y el contenedor viene con Node.js 22.
- **Un cliente de APIs:** Postman o Insomnia. `POST /todos` y `DELETE /todos/1` no se pueden lanzar desde la barra de direcciones del navegador.

## ✅ ¿Cómo compruebas que lo has hecho bien?

En este paquete no hay corrección automática. Ninguna de las 11 carpetas contiene un fichero de test, `learn.json` define `grading` como `incremental` y el ejercicio está registrado como no evaluado. La acción `Build` también está desactivada, así que la forma de validar cada paso es levantar el servidor tú mismo y llamar al endpoint.

El ciclo de trabajo en cada paso es este:

1. Edita `app.js` y guarda.

2. Para el servidor con `Ctrl + C` y vuelve a arrancarlo con `npm run start`. Este proyecto no incluye nodemon, así que `node app.js` no recoge tus cambios por su cuenta.

3. Llama al endpoint y compara la respuesta con la especificación del paso `00`. Para `GET /` y `GET /todos` basta el navegador; para `POST` y `DELETE` usa Postman o Insomnia.

Cinco pasos, el `03`, `05`, `06`, `07` y `08`, traen un `solution.hide.js` con código que funciona y que LearnPack mantiene oculto hasta que lo pides. Los pasos `07.1` y `08.1` muestran la implementación de referencia directamente en las instrucciones, así que si el `POST` o el `DELETE` se te resisten puedes comparar tu versión línea a línea.

## 💡 ¿Qué errores conviene evitar?

1. **Declarar `todos` con `const`.** Añadir una tarea solo muta el array, así que con `const` el paso `07` sigue funcionando. Pero la solución de referencia del `DELETE` reasigna la variable, `todos = todos.filter(...)`, y eso lanza `TypeError: Assignment to constant variable`. Las tres soluciones de referencia que contienen el array, las de los pasos `06`, `07` y `08`, la declaran como `let todos`.

2. **Olvidar `app.use(express.json())`, o ponerlo después de las rutas.** Sin ese middleware Express no parsea el cuerpo JSON y `req.body` llega como `undefined`, con lo que `POST /todos` mete algo inútil en la lista sin avisar. Su sitio es la parte de arriba de `app.js`, antes de definir las rutas.

3. **Usar comparación estricta en el filtro del `DELETE`.** `req.params.todoPosition` llega como la cadena `"1"`, mientras que el índice que te pasa `.filter()` es el número `1`. Si escribes `position !== todoPosition` no se borra nunca nada, porque una cadena jamás es estrictamente igual a un número. Ojo aquí: el ejemplo de `/signup` que aparece en el paso `08` usa `!==`, pero la solución que funciona, la del `08.1`, compara con `!=`.

4. **Crear `app.js` en cualquier sitio menos la raíz.** `package.json` declara `"main": "app.js"` y `"start": "node app.js"`, ambos relativos a la raíz. Si lo metes dentro de una carpeta de ejercicio, `npm run start` falla con `Cannot find module`.

5. **Confundir los dos puertos.** La interfaz de LearnPack corre en el puerto 3000, que es la dirección que imprime la terminal al arrancar el tutorial. Tu API escucha en el 8080, el número que va escrito a mano en `app.listen()`. En Codespaces además tienes que hacer público el puerto 8080 para que Postman pueda llegar desde fuera del contenedor.

6. **Probar `POST` y `DELETE` desde la barra de direcciones.** Escribir una URL en el navegador envía siempre un `GET`. Por eso los pasos `07` y `08` insisten en usar Postman.

7. **Esperar que la lista se guarde.** `todos` es una variable en memoria, no una base de datos. Cada reinicio de `node app.js` tira por la borda lo que hayas creado y deja otra vez los elementos iniciales.

## ❓ Preguntas frecuentes

### ¿Hay que instalar algo para empezar?

No, si abres el repositorio en GitHub Codespaces. El contenedor de desarrollo usa la imagen `javascript-node:22` de Microsoft e instala automáticamente la CLI de LearnPack y su plugin de Node, de forma que el tutorial se abre solo dentro de VS Code. Trabajar en local solo requiere Node.js y dos comandos de `npm`.

### ¿Cómo se prueban los endpoints POST y DELETE?

Con un cliente de APIs como Postman o Insomnia, los dos enlazados desde las instrucciones. Para `POST /todos` pon el método en POST, la URL en `/todos` y el cuerpo en JSON crudo con `{ "done": true, "label": "Start node API tutorial" }`. Para `DELETE` pon el método en DELETE y el índice en la URL, por ejemplo `/todos/0`. Los dos endpoints responden con la lista actualizada.

### ¿Se corrigen los ejercicios automáticamente?

No. Este paquete no tiene ficheros de test y está registrado como ejercicio no evaluado, así que no vas a ver el típico verde o rojo al avanzar por los pasos. Cada paso lo confirmas levantando el servidor y llamando al endpoint, y puedes contrastar tu código con los `solution.hide.js` de los pasos `03`, `05`, `06`, `07` y `08`.

### ¿En qué se diferencian `res.send()` y `res.json()`?

`res.send()` deduce el tipo de contenido a partir de lo que le pasas, y por eso el paso `05` lo usa para devolver la cadena `Hello World!` tal cual. `res.json()` siempre serializa el argumento a JSON y ajusta la cabecera `Content-Type` en consecuencia, que es lo que debe hacer una API REST. En el paso `06` se encadena con el código de estado: `res.status(200).json(todos)`.

### ¿Las tareas sobreviven a un reinicio del servidor?

No. `todos` es un array de JavaScript que vive dentro del proceso de Node, así que todo lo que añadas con `POST /todos` desaparece en cuanto paras el servidor, y el array vuelve a los dos elementos iniciales, `Drink some water` y `Do my homework`. Para conservarlas haría falta una base de datos, algo que este tutorial deja fuera a propósito.

### ¿Cuesta algo y de quién es el código que escribes?

El repositorio es público en GitHub y abrirlo, clonarlo o ejecutarlo no cuesta nada. No incluye ningún fichero `LICENSE`, y en `package.json` solo aparece el campo `"license": "ISC"` que escribe `npm init` por defecto, así que si piensas republicar o redistribuir el contenido del tutorial conviene preguntar antes a 4Geeks Academy. El `app.js` que escribas es tuyo: puedes subirlo a tu propio repositorio y enseñarlo en tu portafolio.

<!-- hide -->
## 📚 Tutoriales relacionados

Paquetes interactivos que encajan bien con este:

1. [Tutorial para Practicar Funciones de Javascript](https://4geeks.com/es/interactive-exercise/javascript-functions-exercises-tutorial-es), si las funciones flecha de los manejadores de ruta te suenan raras.

2. [Ejercicios de arrays y loops de Javascript](https://4geeks.com/es/interactive-exercise/javascript-array-loops-exercises-es), para practicar el `.push()` y el `.filter()` que usas sobre la lista de tareas.

3. [Domina Javascript Practicando](https://4geeks.com/es/interactive-exercise/master-javascript-exercises-es), una tanda más larga sobre el lenguaje en sí.

4. [Curso de React.js desde cero](https://4geeks.com/es/interactive-exercise/curso-react-desde-cero), para construir el frontend que consuma una API como esta.

## 🚀 Cómo empezar

Lo más rápido es [abrirlo en GitHub Codespaces](https://codespaces.new/?repo=4GeeksAcademy/node-express-api-tutorial). El contenedor instala todo y el tutorial arranca solo dentro de VS Code. También puedes abrir el repositorio en [Gitpod](https://gitpod.io#https://github.com/4GeeksAcademy/node-express-api-tutorial).

Si el tutorial no arranca por su cuenta, ejecuta esto en la terminal:

```bash
learnpack start
```

LearnPack imprime la dirección de su interfaz, `http://localhost:3000`, y ahí es donde lees los pasos y avanzas entre ellos. Como tu servidor de Express ocupa la terminal mientras corre, divide la terminal para tener un panel con LearnPack y otro con tu app, tal y como pide el paso `01`:

![Panel de terminal de VS Code con la salida del comando learnpack start, los mensajes Building the exercise index, Downloading the LearnPack coding UI y Exercises are running, el enlace http://localhost:3000, y una flecha roja señalando el botón de dividir la terminal en la esquina superior derecha](https://raw.githubusercontent.com/4GeeksAcademy/node-express-api-tutorial/master/.learn/assets/split-terminal.png)

## 💻 Instalación local

Clona el repositorio y sigue estos pasos:

1. Instala LearnPack y su plugin compilador de Node.js. Necesitas Node.js instalado antes:

   ```bash
   npm i @learnpack/learnpack -g
   learnpack plugins:install @learnpack/node
   ```

2. Arranca el tutorial desde la misma carpeta donde está `learn.json`:

   ```bash
   learnpack start
   ```

3. Instala Express dentro del proyecto, que es además lo que pide el paso `02`:

   ```bash
   npm install express --save-dev
   ```

Si algo falla, la [guía rápida de LearnPack para estudiantes](https://4geeks.com/docs/learnpack/quickstart-for-learners) y las [preguntas frecuentes de LearnPack](https://4geeks.com/en/how-to/faq-learnpack) (en inglés) repasan la instalación completa.

## 📚 Cómo están organizados los ejercicios

Los pasos viven en `.learn/exercises/`, una carpeta cada uno, y se leen en orden numérico:

- **`README.md`:** las instrucciones en inglés.
- **`README.es.md`:** las mismas instrucciones en español. Puedes cambiar de idioma desde el menú sin perder por dónde ibas.
- **`solution.hide.js`:** una versión funcional del fichero en ese punto del tutorial. Está en el `03`, `05`, `06`, `07` y `08`, y LearnPack la mantiene oculta hasta que la pides.

A diferencia de los paquetes con corrección automática, aquí no hay ningún `app.js` dentro de las carpetas de ejercicio ni ningún fichero de test. Creas un único `app.js` en la raíz del repositorio en el paso `03` y lo vas ampliando hasta el final.

## 🤝 Personas que han contribuido

Gracias a quienes han construido y mantienen este paquete, ordenados por número de commits:

1. [tommygonzaleza](https://github.com/tommygonzaleza) 💻

2. [alesanchezr](https://github.com/alesanchezr) 💻

3. [Charlytoc](https://github.com/Charlytoc) 💻

4. [Lorenagubaira](https://github.com/Lorenagubaira) 💻

5. [ehiber](https://github.com/ehiber) 💻

Puedes ver la lista completa en el [gráfico de contribuciones](https://github.com/4GeeksAcademy/node-express-api-tutorial/graphs/contributors). Este proyecto sigue la especificación [all-contributors](https://github.com/kentcdodds/all-contributors) y cualquier tipo de aportación es bienvenida. ¿Has encontrado un fallo o una errata? [Abre un issue](https://github.com/learnpack/learnpack/issues/new) o envía un pull request.
<!-- endhide -->
