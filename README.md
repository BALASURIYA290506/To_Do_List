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
HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>To-Do App</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="todo-container">
    <h1>My To-Do List ✅</h1>
    
    <div class="todo-input">
      <input type="text" id="taskInput" placeholder="Enter a new task...">
      <button id="addTaskBtn">Add</button>
    </div>
    
    <ul id="taskList"></ul>
  </div>

  <!-- Footer Section -->
  <footer>
    <p>Developed by <strong>M BALASURIYA</strong> | Reg. No: <strong>212224240021</strong></p>
  </footer>

  <script src="script.js"></script>
</body>
</html>
```
CSS
```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Arial, sans-serif;
}

body {
  background: #1a1a1a;
  color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.todo-container {
  background: #2a2a2a;
  padding: 20px;
  border-radius: 12px;
  width: 350px;
  box-shadow: 0 4px 15px rgba(0,0,0,0.3);
}

h1 {
  text-align: center;
  margin-bottom: 15px;
}

.todo-input {
  display: flex;
  gap: 10px;
}

#taskInput {
  flex: 1;
  padding: 10px;
  border: none;
  border-radius: 6px;
  outline: none;
}

#addTaskBtn {
  padding: 10px 15px;
  border: none;
  border-radius: 6px;
  background: #4CAF50;
  color: white;
  cursor: pointer;
}

#addTaskBtn:hover {
  background: #45a049;
}

ul {
  list-style: none;
  margin-top: 15px;
}

li {
  background: #333;
  padding: 10px;
  border-radius: 6px;
  margin-bottom: 8px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

li.completed {
  text-decoration: line-through;
  opacity: 0.6;
}
footer {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  text-align: center;
  background: #111;
  color: #bbb;
  padding: 10px;
  font-size: 14px;
  border-top: 1px solid #444;
}

footer strong {
  color: #4CAF50;
}
```
JAVASCRIPT
```js
const taskInput = document.getElementById("taskInput");
const addTaskBtn = document.getElementById("addTaskBtn");
const taskList = document.getElementById("taskList");

// Load saved tasks on page load
document.addEventListener("DOMContentLoaded", loadTasks);

addTaskBtn.addEventListener("click", addTask);
taskInput.addEventListener("keypress", function(e) {
  if (e.key === "Enter") addTask();
});

function addTask() {
  const taskText = taskInput.value.trim();
  if (taskText === "") return;

  const li = document.createElement("li");
  li.innerHTML = `
    <span class="task">${taskText}</span>
    <button class="deleteBtn">❌</button>
  `;

  // Toggle complete
  li.querySelector(".task").addEventListener("click", () => {
    li.classList.toggle("completed");
    saveTasks();
  });

  // Delete task
  li.querySelector(".deleteBtn").addEventListener("click", () => {
    li.remove();
    saveTasks();
  });

  taskList.appendChild(li);
  taskInput.value = "";
  saveTasks();
}

function saveTasks() {
  localStorage.setItem("tasks", taskList.innerHTML);
}

function loadTasks() {
  taskList.innerHTML = localStorage.getItem("tasks") || "";
  // Reattach event listeners after reload
  document.querySelectorAll(".task").forEach(task => {
    task.addEventListener("click", () => {
      task.parentElement.classList.toggle("completed");
      saveTasks();
    });
  });
  document.querySelectorAll(".deleteBtn").forEach(btn => {
    btn.addEventListener("click", () => {
      btn.parentElement.remove();
      saveTasks();
    });
  });
}
```


## OUTPUT
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/9cc847d3-ae84-41ea-8862-0fc41bb9d077" />


## RESULT
The program for creating To-do list using JavaScript is executed successfully.
