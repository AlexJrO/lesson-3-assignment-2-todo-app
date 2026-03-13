# lesson-3-assignment-2-todo-app[
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Simple To-Do App</title>
<link rel="stylesheet" href="style.css">
</head>

<body>

<h1>My Simple To-Do List</h1>

<!-- input where user type the task -->
<input type="text" id="taskInput" placeholder="Write a task">

<!-- button to add the task -->
<button id="addBtn">Add Task</button>

<!-- list where tasks will appear -->
<ul id="taskList"></ul>

<script src="script.js"></script>

</body>
</html>
body{
font-family: Arial;
background:#f5f5f5;
text-align:center;
margin-top:40px;
}

input{
padding:8px;
width:200px;
}

button{
padding:8px;
cursor:pointer;
}

li{
list-style:none;
background:white;
margin:10px auto;
padding:10px;
width:300px;
display:flex;
justify-content:space-between;
}

.completed{
text-decoration:line-through;
color:gray;
}
// selecting elements from the HTML page
const input = document.getElementById("taskInput");
const button = document.getElementById("addBtn");
const list = document.getElementById("taskList");


// this function creates a new task
function addTask(){

// get the text from input
const text = input.value;

// if input is empty do nothing
if(text === ""){
alert("Please type a task");
return;
}

// create new list item
const li = document.createElement("li");

// put the text inside the list item
li.textContent = text;


// button to mark task completed
const doneBtn = document.createElement("button");
doneBtn.textContent = "Done";

// when click it marks as completed
doneBtn.addEventListener("click", function(){
li.classList.toggle("completed");
});


// button to delete task
const deleteBtn = document.createElement("button");
deleteBtn.textContent = "Remove";

// when click it removes the task
deleteBtn.addEventListener("click", function(){
li.remove();
});


// add buttons to the task
li.appendChild(doneBtn);
li.appendChild(deleteBtn);

// add task to the list on page
list.appendChild(li);

// clear input
input.value="";
}


// event listener when user click button
button.addEventListener("click", addTask);
