# To-Do List Application

## **Overview**

This repository contains a simple To-Do List application built with HTML, CSS, and JavaScript. The app allows users to add, edit, and remove tasks, making it easy to manage daily activities and stay organized.

**Features:**
- Add new tasks with a descriptive title
- Mark tasks as complete or incomplete
- Edit existing tasks
- Remove tasks from the list
- Responsive design for mobile and desktop devices

## **Preview**

[![To-Do List Screenshot](screenshot.png)](https://your-username.github.io/your-repository-name/)

**Live Demo:** [Try the To-Do List App](https://your-username.github.io/your-repository-name/)

Explore the interactive To-Do List application and manage your tasks efficiently directly from your browser.

## **Code**

### **HTML**
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta name="description" content="We love JavaScript" />
    <title>DOM - Document Object Model</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <section class="container">
      <div class="logo">
        <img id="img-size" src="images/logo-colored-removebg-preview.png" alt="Always with Junior" />
      </div>
      <h1 id="header" class="header">To-Do App</h1>

      <form class="new-task-container box">
        <label for="new-task">Add New Task</label>
        <input type="text" id="new-task" />
        <input type="submit" id="addTask" value="Add Task" />
      </form>

      <div class="todo-list box">
        <h2>Incomplete Tasks</h2>
        <ul id="items">
          <li class="item">
            <input type="checkbox" /><label>Task Name</label>
          </li>
          <li class="item">
            <input type="checkbox" /><label>Task Name</label>
          </li>
          <li class="item">
            <input type="checkbox" /><label>Task Name</label>
          </li>
        </ul>
      </div>
      <!--/todo-list-->

      <div class="complete-list box">
        <h2>Completed Tasks</h2>
        <ul id="complete-ul">
          <li class="item">Task Name <button class="delete">Delete</button></li>
        </ul>
      </div>
      <!--/complete-list-->
    </section>
    <!--/container-->
    <script src="script.js"></script>
  </body>
</html>
```
### **CSS**
```css
/*
 * Title: To Do List CSS file
 * Description: This file has all the styles associated with the To Do App project
 * Author: Sumit Saha ( Learn with Sumit )
 * Date: 12/16/2020
 *
 */

* {
  box-sizing: border-box;
}

.container {
  background: #c5b1c9;
  padding: 25px;
  max-width: 760px;
  margin: 25px auto;
  overflow: hidden;
  border-radius: 10px;
  border: 4px solid #d67de7;
  font-family: sans-serif;
}
#img-size{
  height: 200px;
  width: max-content;
}
h1,
h2 {
  margin: 0;
  text-align: center;
  text-transform: uppercase;
}

h2 {
  font-size: 20px;
  text-align: center;
  border-bottom: 1px solid #d67de7;
  padding: 0 0 10px;
  color: #57635c;
}

.logo {
  width: 100%;
  text-align: center;
}

#img-size{
  width: max-content;
}
.new-task-container {
  text-align: center;
}

.box {
  padding: 10px 15px;
  border: 2px solid #d67de7;
  border-radius: 5px;
  background: #fff;
  margin: 15px 0;
}

.todo-list {
  float: left;
  width: 46%;
}

.complete-list {
  float: right;
  width: 46%;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

li {
  padding: 10px;
  border-bottom: 1px dotted #ccc;
}

.update {
  float: right;
  background-color: blue;
  color: white;
  border: 0px;
  padding: 3px 5px;
}

.delete {
  float: right;
  background-color: red;
  color: white;
  border: 0px;
  padding: 3px 5px;
}
```
### **JS**
```js
/*
 * Title: To Do Application using vanilla JS DOM
 * Description: This JS file has all the JS functions necessary to control the to do application
 *
 */

 // select elements & assign them to variables
// select elements & assign them to variables
let newTask = document.querySelector('#new-task');
let form = document.querySelector('form');
let todoUl = document.querySelector('#items');
let completeUl = document.querySelector('.complete-list ul');


// functions
let createTask = function(task) {
   let listItem = document.createElement('li');
   let checkBox = document.createElement('input');
   let label = document.createElement('label');

   label.innerText = task;
   checkBox.type = 'checkbox';

   listItem.appendChild(checkBox);
   listItem.appendChild(label);

   return listItem;
}

let addTask = function(event) {
   event.preventDefault();
   let listItem = createTask(newTask.value);
   todoUl.appendChild(listItem);
   newTask.value = "";
   // bind the new list item to the incomplete list
   bindInCompleteItems(listItem, completeTask);
}

let completeTask = function() {
   let listItem = this.parentNode;
   let deleteBtn = document.createElement('button');
   deleteBtn.innerText = 'Delete';
   deleteBtn.className = 'delete';
   listItem.appendChild(deleteBtn);

   let checkBox = listItem.querySelector('input[type="checkbox"]');
   checkBox.remove();
   completeUl.appendChild(listItem);
   bindCompleteItems(listItem, deleteTask);
}

let deleteTask = function() {
   let listItem = this.parentNode;
   let ul = listItem.parentNode;
   ul.removeChild(listItem);
}

let bindInCompleteItems = function(taskItem, checkboxClick) {
   let checkBox = taskItem.querySelector('input[type="checkbox"]');
   checkBox.onchange = checkboxClick;
}

let bindCompleteItems = function(taskItem, deleteButtonClick) {
   let deleteButton = taskItem.querySelector('.delete');
   deleteButton.onclick = deleteButtonClick;
}

for(let i=0; i< todoUl.children.length; i++ ) {
   bindInCompleteItems(todoUl.children[i], completeTask);
}

for(let i=0; i< completeUl.children.length; i++ ) {
   bindCompleteItems(completeUl.children[i], deleteTask);
}

form.addEventListener('submit', addTask);
```
### **Blame**

- **HTML:** Constructs the main layout of the To-Do List application, including the input field, button, and task list.
- **CSS:** Styles the application for a clean and responsive user interface, ensuring a pleasant visual experience.
- **JavaScript:** Manages the interactive features, such as adding tasks to the list, handling user input, and updating the task display.

