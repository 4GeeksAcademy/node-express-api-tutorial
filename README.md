# Welcome to Node API Tutorial

This is an interactive tutorial that will teach you how to create an API with Node and Express.

## 🌱 How to start this project?

This project comes with the necessary files to start working, but you have two options to start:

a) Open this link in your browser to clone it with gitpod: https://gitpod.io#https://github.com/breatheco-de/node-api-tutorial

b) You can clone this repository on your local computer:
```sh
$ git clone https://github.com/breatheco-de/node-api-tutorial
```
> Type `$ learnpack start` in your terminal to start the exercises.

💡 Important: Remember to create a new repository, update the remote (`git remote set-url origin <your new url>`), and upload the code to your new repository using `add`, `commit` and `push`.


## About the project we are going to build

In this tutorial we are going to be building a REST API that exposes 3 endpoints to the internet:

```txt
GET /todos
POST /todos
DELETE /todos/<int:position>
```

### GET /todos

Will return the list of all todos like this:

```javascript
[
    {
        "done": true,
        "label": "Sample Todo 1"
    },
    {
        "done": true,
        "label": "Sample Todo 2"
    }
]
```

### POST /todos

It's going to add a new todo to the list, it will receive the following request body:

```javascript
{
    "done": true,
    "label": "Sample Todo 1"
}
```

And return the updated list of todos.

### DELETE /todos/<int:position>

It's going to remove one todo based on a given position at the end of the url, and return the updated list of todos.
