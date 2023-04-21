## DOCUMENTATION OF THE PROJECT3-MERN IMPLEMENTATION

`sudo apt update`

`sudo apt upgrade`

`curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -`

`sudo apt-get install -y nodejs`

![Node.js installation](./images/Install%20Node.js%20on%20the%20server.PNG)

## INSTALL EXPRESSJS-It is framework for Node.js

## To use expreesjs, install it use npm;

`npm install express`

![express installation](./images/installing-express.PNG)

## create a file index.js with the command below

`touch index.js`

![Ndex.js file](./images/Ndex.js%20status.PNG)

## Install the dotenv module

`npm install dotenv`

![dotenv](./images/Installing%20dotenv.PNG)

## Open the index.js file with

`vim index.js`

## start our server to see if it works

`node index.js`

![Server running](./images/Server%20status.PNG)

## Open up your browser and try to access your server

`http://<PublicIP-or-PublicDNS>:5000`

![access the Server](./images/Webpage.PNG)



## TO DO LIST APPLICATION

1. Create a new task
2. Display list of all tasks
3. Delete a completed task

## Each task will be associated with some particular endpoint and will use different standard HTTP request methods: POST, GET, DELETE.

## For each task, we need to create routes that will define various endpoints that the To-do app will depend on. So let us create a folder routes


`mkdir routes`

## Change directory to routes folder

`cd routes`

## create a file api.js

`touch api.js`

![apifile](./images/Fileapi.js)


`vm api.js`

## create a Model since the app is going to use mongodb. A model is at the heart of JavaScript based applications, and it is what makes it interactive. We will also use models to define the database schema . This is important so that we will be able to define the fields stored in each Mongodb document. To create a Schema and a model, install mongoose which is a Node.js package that makes working with mongodb easier.

`npm install mongoose`

![mongoose](./images/Mongoose%20installed.PNG)

## Create a new models

`mkdir models`

`cd models`

`touch todo.js`

`vim todo.js`

`const mongoose = require('mongoose');
const Schema = mongoose.Schema;

//create schema for todo
const TodoSchema = new Schema({
action: {
type: String,
required: [true, 'The todo text field is required']
}
})

//create model for todo
const Todo = mongoose.model('todo', TodoSchema);

module.exports = Todo;`


`vim api.js`

`const express = require ('express');
const router = express.Router();
const Todo = require('../models/todo');

router.get('/todos', (req, res, next) => {

//this will return all the data, exposing only the id and action field to the client
Todo.find({}, 'action')
.then(data => res.json(data))
.catch(next)
});

router.post('/todos', (req, res, next) => {
if(req.body.action){
Todo.create(req.body)
.then(data => res.json(data))
.catch(next)
}else {
res.json({
error: "The input field is empty"
})
}
});

router.delete('/todos/:id', (req, res, next) => {
Todo.findOneAndDelete({"_id": req.params.id})
.then(data => res.json(data))
.catch(next)
})

module.exports = router;`

## MONGODB DATABASE

## 

