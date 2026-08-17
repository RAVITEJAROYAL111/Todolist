# Ex03 To-Do List using JavaScript
## Date:

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
```
index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do Application</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<div class="container">
    <h2>To-Do Application</h2>

    <div class="input-group">
        <input type="text" id="taskInput" placeholder="Enter a Task">
        <button onclick="addTask()">Add</button>
    </div>

    <input type="text" id="search" class="search"
           placeholder="Search Task..."
           onkeyup="searchTask()">

    <ul id="taskList"></ul>

    <button class="clear-btn" onclick="clearAll()">Clear All</button>
</div>

<script src="script.js"></script>
</body>
</html>
``
style.css
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial,sans-serif;
}

body{
    background:#f4f4f4;
    display:flex;
    justify-content:center;
    align-items:center;
    height:100vh;
}

.container{
    width:450px;
    background:#fff;
    padding:20px;
    border-radius:10px;
    box-shadow:0 0 10px rgba(0,0,0,0.2);
}

h2{
    text-align:center;
    margin-bottom:20px;
    color:#333;
}

.input-group{
    display:flex;
    gap:10px;
}

.input-group input{
    flex:1;
    padding:10px;
}

button{
    padding:10px 15px;
    cursor:pointer;
    border:none;
    background:#007BFF;
    color:white;
    border-radius:5px;
}

button:hover{
    background:#0056b3;
}

.search{
    width:100%;
    padding:10px;
    margin:15px 0;
}

ul{
    list-style:none;
}

li{
    display:flex;
    justify-content:space-between;
    align-items:center;
    background:#eee;
    margin:8px 0;
    padding:10px;
    border-radius:5px;
}

.completed{
    text-decoration:line-through;
    color:gray;
}

.actions button{
    margin-left:5px;
    padding:5px 10px;
}

.clear-btn{
    margin-top:15px;
    width:100%;
}
````
script.js

function addTask() {

    let input = document.getElementById("taskInput");
    let task = input.value.trim();

    if (task === "") {
        alert("Please enter a task.");
        return;
    }

    let li = document.createElement("li");

    li.innerHTML = `
        <span>${task}</span>
        <div class="actions">
            <button onclick="completeTask(this)">✔</button>
            <button onclick="editTask(this)">Edit</button>
            <button onclick="deleteTask(this)">Delete</button>
        </div>
    `;

    document.getElementById("taskList").appendChild(li);

    input.value = "";
}

function completeTask(button) {
    button.parentElement.parentElement
          .querySelector("span")
          .classList.toggle("completed");
}

function editTask(button) {

    let span = button.parentElement.parentElement.querySelector("span");

    let newTask = prompt("Edit Task:", span.innerText);

    if (newTask !== null && newTask.trim() !== "") {
        span.innerText = newTask;
    }
}

function deleteTask(button) {
    button.parentElement.parentElement.remove();
}

function clearAll() {
    document.getElementById("taskList").innerHTML = "";
}

function searchTask() {

    let filter = document.getElementById("search").value.toLowerCase();

    let tasks = document.querySelectorAll("#taskList li");

    tasks.forEach(function(task) {

        let text = task.querySelector("span").innerText.toLowerCase();

        if (text.includes(filter)) {
            task.style.display = "flex";
        } else {
            task.style.display = "none";
        }
    });
}
````

## OUTPUT
<img width="1037" height="511" alt="image" src="https://github.com/user-attachments/assets/7f051f8d-0ff3-4222-b4aa-a699c19952b1" />


## RESULT
The program for creating To-do list using JavaScript is executed successfully.
