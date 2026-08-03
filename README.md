<!-- hide -->
<div align="center">

# Node API Tutorial

<img width="560" alt="Tutorial cover on a cream background: the words Learn Node EXPRESS Interactive in large grey letters, next to a white hand icon clicking a button with purple signal waves around it, and the address www.4geeks.com on a black bar at the bottom" src="https://raw.githubusercontent.com/4GeeksAcademy/node-express-api-tutorial/master/.learn/assets/preview.png">

[![Interactive tutorial](https://img.shields.io/badge/4Geeks_Academy-Interactive_tutorial-2563eb)](https://4geeks.com/en/learnpack)
[![Built with LearnPack](https://img.shields.io/badge/LearnPack-11_guided_steps-2563eb)](https://github.com/learnpack/learnpack)
[![Open in GitHub Codespaces](https://img.shields.io/badge/Open_in-GitHub_Codespaces-fb5a1f)](https://codespaces.new/?repo=4GeeksAcademy/node-express-api-tutorial)

Read these instructions in [🇪🇸 Spanish](https://github.com/4GeeksAcademy/node-express-api-tutorial/blob/HEAD/README.es.md)

</div>
<!-- endhide -->

This LearnPack tutorial builds a REST API with Node.js and Express in 11 guided steps, ending in an `app.js` of about 30 lines that exposes `GET /todos`, `POST /todos` and `DELETE /todos/:todoPosition` over an in-memory array on port 8080. It is rated easy, estimated at 8 hours, has no automated tests, and every step ships instructions in English and Spanish.

<!-- hide -->
## 📋 About this tutorial

- **Difficulty:** easy. It starts before Express is even installed, so no backend experience is assumed.
- **Estimated duration:** 8 hours.
- **Technologies:** JavaScript, Node.js, Express 4.18, the command line, REST APIs.
- **Steps:** 11 folders inside `.learn/exercises/`, numbered `00` to `08.1`.
- **Grading:** none. There is no test file in the package, so nothing is corrected automatically.
- **Reference solutions:** 5 of the 11 steps include a `solution.hide.js` file you can reveal.
- **Video solutions:** none. `videoSolutions` is set to `false` in `learn.json`.
- **Languages:** every step ships with `README.md` and `README.es.md`.
<!-- endhide -->

## 🎯 What will you learn?

The tutorial teaches the backend half of a web application, one idea per step:

- **The Node.js toolchain from the terminal:** checking your version with `node -v`, installing a package with `npm install express --save-dev`, and launching your program with `npm run start`.
- **What Express actually is:** the framework you load with `require('express')` and instantiate with `express()` to get the `app` object that everything else hangs from.
- **Starting an HTTP server:** `app.listen(8080, callback)`, and reading the port back out of `server.address().port` to log it.
- **Routing:** `app.get()`, `app.post()` and `app.delete()`, and the `(req, res)` handler signature they all share.
- **Answering with text versus answering with JSON:** `res.send('Hello World!')` for a plain string, `res.status(200).json(todos)` for the JSON that a REST API is supposed to return.
- **Reading the request body:** why `app.use(express.json())` has to be registered, and how the parsed object arrives in `req.body`.
- **Reading URL parameters:** declaring `:todoPosition` in the route and picking it up from `req.params.todoPosition`.
- **Keeping state in memory:** a plain JavaScript array mutated with `.push()` to add and rebuilt with `.filter()` to delete.
- **Testing an API with no frontend:** sending requests with Postman, Insomnia or any other API request builder, because a browser address bar can only send `GET`.

## 👀 What will you build?

A single To-Do REST API with three endpoints:

```txt
GET    /todos
POST   /todos
DELETE /todos/<position>
```

You write everything into one `app.js` file at the root of the project, and each step adds a few lines to the previous ones. These are the 11 folders:

1. **`00` Welcome:** the specification you are going to implement, with the exact JSON shape of a todo, `{ "done": true, "label": "Sample Todo 1" }`, and what each of the three endpoints must return.

2. **`01` Installing Node:** split the terminal, run `node -v`, and install Node.js from nodejs.org if no version is printed.

3. **`02` Installing Express:** `npm install express --save-dev`. The tutorial uses `--save-dev` so Express is recorded in the project's dependencies.

4. **`03` First Express App:** create `app.js` in the root of the project with the four lines everything else needs: the `require`, the `express()` call, `app.use(express.json())` and `app.listen(8080, ...)`.

5. **`04` Run your app:** `npm run start`, which is already wired in `package.json` to execute `node app.js`.

6. **`05` Your First Route:** add `app.get('/', (req, res) => { res.send('Hello World!') })` and open port 8080 to see the string in the browser.

7. **`06` Returning JSON:** declare a global `todos` array containing at least `{ "label": "Drink some water", "done": false }`, and add `GET /todos` answering with `res.status(200).json(todos)`.

8. **`07` Post Todo:** your first endpoint written from scratch. A `POST /todos` that takes the todo from the request body, adds it to the list and returns the updated list. The step gives you a `POST /signup` example to model it on.

9. **`07.1` Check post todo:** the reference implementation, built on `req.body`, `todos.push(todo)` and `res.status(200).json(todos)`, plus the exact request to fire from Postman with the body `{ "done": true, "label": "Start node API tutorial" }`.

10. **`08` Delete Todo:** the second endpoint you write yourself. A `DELETE /todos/:todoPosition` that reads the position from the URL and removes that item from the list.

11. **`08.1` Check delete todo:** the reference implementation, which reassigns `todos = todos.filter((value, position) => position != todoPosition)` and returns the shortened list.

## 🎓 What do you need before starting?

- **Basic JavaScript:** declaring variables, arrays of objects and arrow functions. The tutorial explains Express, not the language.
- **A terminal you are not afraid of:** every step from `01` to `04` is a command, and the server runs in the foreground while you work.
- **Nothing installed, if you use Codespaces:** the dev container is built on the `javascript-node:22` image and installs the LearnPack CLI and its Node plugin on creation.
- **Node.js, if you work locally:** any modern version. Step `01` shows `v.16.14.0` as sample output, and the dev container ships Node.js 22.
- **An API request builder:** Postman or Insomnia. You cannot exercise `POST /todos` or `DELETE /todos/1` from the browser address bar.

## ✅ How do you check your work?

There is no automatic grading in this package. None of the 11 folders contains a test file, `learn.json` sets `grading` to `incremental`, and the asset is registered as not graded. The `Build` action is disabled too, so the way you verify a step is by running the server yourself and calling the endpoint.

That means the loop for every step is:

1. Edit `app.js` and save.

2. Stop the running server with `Ctrl + C` and start it again with `npm run start`. There is no nodemon in this project, so `node app.js` will not pick up your changes on its own.

3. Call the endpoint and compare it against the specification in `00 Welcome`. A browser is enough for `GET /` and `GET /todos`; use Postman or Insomnia for `POST` and `DELETE`.

Five steps, `03`, `05`, `06`, `07` and `08`, ship a `solution.hide.js` with working code that LearnPack keeps hidden until you ask for it. Steps `07.1` and `08.1` print the reference implementation directly in the instructions, so if `POST` or `DELETE` fights back you can compare your version line by line.

## 💡 What mistakes should you avoid?

1. **Declaring `todos` with `const`.** Adding a todo only mutates the array, so `const` survives step `07`. But the reference solution for `DELETE` reassigns the variable, `todos = todos.filter(...)`, and that throws `TypeError: Assignment to constant variable`. The three reference solutions that contain the array, steps `06`, `07` and `08`, all declare it as `let todos`.

2. **Forgetting `app.use(express.json())`, or registering it after your routes.** Without that middleware Express does not parse the JSON body and `req.body` is `undefined`, so `POST /todos` silently pushes nothing useful into the list. It belongs near the top of `app.js`, before the route definitions.

3. **Using strict comparison in the `DELETE` filter.** `req.params.todoPosition` arrives as the string `"1"`, while the index that `.filter()` hands you is the number `1`. Write `position !== todoPosition` and nothing is ever deleted, because a string is never strictly equal to a number. Careful here: the `/signup` example printed in step `08` uses `!==`, but the working solution in `08.1` compares with `!=`.

4. **Creating `app.js` somewhere other than the project root.** `package.json` declares `"main": "app.js"` and `"start": "node app.js"`, both relative to the root. Put the file inside an exercise folder and `npm run start` fails with `Cannot find module`.

5. **Confusing the two ports.** LearnPack's own interface runs on port 3000, which is the address the terminal prints when you start the tutorial. Your API listens on 8080, the number hardcoded in `app.listen()`. In Codespaces you also have to make port 8080 public before Postman can reach it from outside the container.

6. **Testing `POST` and `DELETE` from the address bar.** Typing a URL in a browser always sends a `GET`. Both steps `07` and `08` remind you to use Postman for exactly this reason.

7. **Expecting the list to be saved.** `todos` is a variable in memory, not a database. Every restart of `node app.js` throws away whatever you posted and puts the initial items back.

## ❓ Frequently asked questions

### Do I need to install anything to start?

No, if you open the repository in GitHub Codespaces. The dev container uses Microsoft's `javascript-node:22` image and installs the LearnPack CLI plus its Node plugin automatically, so the tutorial opens by itself inside VS Code. Working locally only needs Node.js and two `npm` commands.

### How do I test the POST and DELETE endpoints?

With an API request builder such as Postman or Insomnia, both linked from the instructions. For `POST /todos` set the method to POST, the URL to `/todos` and the raw JSON body to `{ "done": true, "label": "Start node API tutorial" }`. For `DELETE` set the method to DELETE and put the index in the URL, like `/todos/0`. Both endpoints answer with the updated list.

### Are my exercises graded automatically?

No. This package has no test files, and it is registered as a non-graded exercise, so there is no red or green feedback when you click through the steps. You confirm each step by running the server and calling the endpoint, and you can compare against the `solution.hide.js` files in steps `03`, `05`, `06`, `07` and `08`.

### What is the difference between `res.send()` and `res.json()`?

`res.send()` guesses the content type from what you pass it, which is why step `05` uses it to return the plain string `Hello World!`. `res.json()` always serialises the argument to JSON and sets the `Content-Type` header accordingly, which is what a REST API has to do. Step `06` chains it with the status code, `res.status(200).json(todos)`.

### Do the todos survive a server restart?

They do not. `todos` is a plain JavaScript array living in the Node process, so anything you add with `POST /todos` disappears the moment you stop the server, and the array goes back to the two starter items, `Drink some water` and `Do my homework`. Persisting them would need a database, which this tutorial deliberately leaves out.

### Does it cost anything, and who owns the code I write?

The repository is public on GitHub and nothing is charged to open, clone or run it. It ships no `LICENSE` file, and `package.json` only carries the default `"license": "ISC"` field that `npm init` writes, so if you plan to republish or redistribute the tutorial content itself, ask 4Geeks Academy first. The `app.js` you write is yours to keep, push to your own repository and put in your portfolio.

<!-- hide -->
## 📚 Related tutorials

Interactive packages that pair well with this one:

1. [Practice Javascript Functions Tutorial](https://4geeks.com/en/interactive-exercise/javascript-functions-exercises-tutorial), if the arrow functions in the route handlers feel unfamiliar.

2. [Learn Javascript Arrays and Loops Interactive](https://4geeks.com/en/interactive-exercise/javascript-array-loops-exercises), for the `.push()` and `.filter()` used on the `todos` list.

3. [Master Javascript Practicing](https://4geeks.com/en/interactive-exercise/master-javascript-exercises), a longer drill on the language itself.

4. [Learn React.js Tutorial and Interactive Exercises](https://4geeks.com/en/interactive-exercise/react-js-tutorial-exercises), to build the frontend that consumes an API like this one.

## 🚀 How to start

The fastest way is [Open in GitHub Codespaces](https://codespaces.new/?repo=4GeeksAcademy/node-express-api-tutorial). The container installs everything and the tutorial opens on its own inside VS Code. You can also open the repository in [Gitpod](https://gitpod.io#https://github.com/4GeeksAcademy/node-express-api-tutorial).

If the tutorial does not start by itself, run this in the terminal:

```bash
learnpack start
```

LearnPack prints the address of its interface, `http://localhost:3000`, and that is where you read the steps and move between them. Because your Express server occupies the terminal while it runs, split the terminal so you keep one panel for LearnPack and another one for your app, exactly as step `01` asks:

![VS Code terminal panel showing the output of the learnpack start command, with the messages Building the exercise index, Downloading the LearnPack coding UI, Exercises are running and the link http://localhost:3000, and a red arrow pointing at the split terminal button in the top right corner](https://raw.githubusercontent.com/4GeeksAcademy/node-express-api-tutorial/master/.learn/assets/split-terminal.png)

## 💻 Local installation

Clone the repository and follow these steps:

1. Install LearnPack and its Node.js compiler plugin. You need Node.js installed first:

   ```bash
   npm i @learnpack/learnpack -g
   learnpack plugins:install @learnpack/node
   ```

2. Start the tutorial from the same folder where `learn.json` lives:

   ```bash
   learnpack start
   ```

3. Install Express inside the project, which is also what step `02` asks you to do:

   ```bash
   npm install express --save-dev
   ```

If something goes wrong, the [LearnPack quickstart for learners](https://4geeks.com/docs/learnpack/quickstart-for-learners) and the [LearnPack FAQ](https://4geeks.com/en/how-to/faq-learnpack) walk through the whole setup.

## 📚 How the exercises are organized

The steps live in `.learn/exercises/`, one folder each, and they are read in numeric order:

- **`README.md`:** the instructions in English.
- **`README.es.md`:** the same instructions in Spanish. You can switch language from the menu without losing your place.
- **`solution.hide.js`:** a working version of the file at that point of the tutorial, present in `03`, `05`, `06`, `07` and `08` and hidden by LearnPack until you ask for it.

Unlike the graded packages, there is no `app.js` inside the exercise folders and no test file anywhere. You create a single `app.js` at the root of the repository in step `03` and keep growing it until the end.

## 🤝 Contributors

Thanks to the people who built and maintain this package, listed by number of commits:

1. [tommygonzaleza](https://github.com/tommygonzaleza) 💻

2. [alesanchezr](https://github.com/alesanchezr) 💻

3. [Charlytoc](https://github.com/Charlytoc) 💻

4. [Lorenagubaira](https://github.com/Lorenagubaira) 💻

5. [ehiber](https://github.com/ehiber) 💻

See the full list on the [contributors graph](https://github.com/4GeeksAcademy/node-express-api-tutorial/graphs/contributors). This project follows the [all-contributors](https://github.com/kentcdodds/all-contributors) specification and contributions of any kind are welcome. Found a bug or a typo? [Open an issue](https://github.com/learnpack/learnpack/issues/new) or send a pull request.
<!-- endhide -->
