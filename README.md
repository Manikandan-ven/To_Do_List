# Ex03 To-Do List using JavaScript
## Date:10/03/2026

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
index.html
~~~
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Vintage Green To-Do List</title>
<link rel="stylesheet" href="style.css">
</head>

<body>

<div class="notebook">

<h1>📒 My Vintage To-Do List</h1>

<div class="input-section">
<input type="text" id="taskInput" placeholder="Write your task...">
<button onclick="addTask()">Add</button>
</div>

<ul id="taskList"></ul>

</div>

<script src="script.js"></script>

</body>
</html>
~~~
style.css
~~~
/* Vintage Green Notebook Theme */

body{
font-family:'Georgia',serif;
background:#3e5c4b;
display:flex;
justify-content:center;
align-items:center;
height:100vh;
margin:0;
}

.notebook{
background:#e6dbc5;
padding:40px 30px;
width:420px;
border-radius:10px;
border:2px solid #6b8e73;
box-shadow:5px 5px 20px rgba(0,0,0,0.4);
}

h1{
text-align:center;
color:#2f4f4f;
margin-bottom:25px;
}

.input-section{
display:flex;
gap:10px;
margin-bottom:20px;
}

input{
flex:1;
padding:10px;
border:2px solid #6b8e73;
border-radius:6px;
background:#f9f6ef;
font-size:15px;
}

button{
background:#6b8e73;
color:white;
border:none;
padding:10px 15px;
border-radius:6px;
cursor:pointer;
font-weight:bold;
}

button:hover{
background:#557a63;
}

ul{
list-style:none;
padding:0;
}

li{
display:flex;
justify-content:space-between;
padding:12px;
margin-bottom:10px;
background:#f1e7d3;
border-left:5px solid #6b8e73;
}

.completed{
text-decoration:line-through;
color:#777;
}

li button{
background:none;
border:none;
color:#cc3333;
font-weight:bold;
cursor:pointer;
}
~~~
script.js
~~~
function addTask(){

const input=document.getElementById("taskInput");
const taskText=input.value.trim();

if(!taskText){
alert("Please write a task!");
return;
}

const li=document.createElement("li");
li.textContent=taskText;

li.addEventListener("click",()=>{
li.classList.toggle("completed");
saveTasks();
});

const delBtn=document.createElement("button");
delBtn.textContent="✖";

delBtn.onclick=()=>{
li.remove();
saveTasks();
};

li.appendChild(delBtn);

document.getElementById("taskList").appendChild(li);

input.value="";

saveTasks();
}

function saveTasks(){

const tasks=[];

document.querySelectorAll("#taskList li").forEach(li=>{
tasks.push({
text:li.firstChild.textContent,
completed:li.classList.contains("completed")
});
});

localStorage.setItem("tasks",JSON.stringify(tasks));
}

function loadTasks(){

const stored=JSON.parse(localStorage.getItem("tasks")||"[]");

stored.forEach(task=>{

const li=document.createElement("li");
li.textContent=task.text;

if(task.completed){
li.classList.add("completed");
}

li.addEventListener("click",()=>{
li.classList.toggle("completed");
saveTasks();
});

const delBtn=document.createElement("button");
delBtn.textContent="✖";

delBtn.onclick=()=>{
li.remove();
saveTasks();
};

li.appendChild(delBtn);

document.getElementById("taskList").appendChild(li);

});
}
window.onload=loadTasks;
~~~
## OUTPUT
![alt text](<Screenshot 2026-03-10 121548.png>)






















## RESULT
The program for creating To-do list using JavaScript is executed successfully.
