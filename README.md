# Ex03 To-Do List using JavaScript
## Date:03-09-2025

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
html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List</title>
    <link rel="stylesheet" href="todo.css">
</head>
<body>

    <div class="container">
        <div class="todo-app">
            <h2>To-Do List 📝</h2>
            <div class="row">
                <input type="text" id="input-box" placeholder="Add your task">
                <button onclick="addTask()">Add</button>
            </div>
            
            <div class="filter-controls">
                <button id="all-btn" class="active">All</button>
                <button id="completed-btn">Completed</button>
                <button id="clear-btn">Clear</button>
            </div>
            
            <ul id="list-container">
            </ul>
        </div>
    </div>

    <script src="todo.js"></script>
</body>
</html>
```
css
```
* {
    margin: 0;
    padding: 0;
    font-family: 'Poppins', sans-serif;
    box-sizing: border-box;
}

body {
    background: #000000;
    background: url('pro.jpg'); 
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
}

.container {
    width: 100%;
    min-height: 100vh;
    padding: 10px;
}

.todo-app {
    width: 100%;
    max-width: 540px;
    background: rgba(255, 255, 255, 0.9); 
    margin: 100px auto 20px;
    padding: 40px 30px 70px;
    border-radius: 10px;
}

.todo-app h2 {
    color: #002765;
    display: flex;
    align-items: center;
    margin-bottom: 20px;
}

.todo-app h2 img {
    width: 30px;
    margin-left: 10px;
}

.row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: #edeef0;
    border-radius: 30px;
    padding-left: 20px;
    margin-bottom: 25px;
}

input {
    flex: 1;
    border: none;
    outline: none;
    background: transparent;
    padding: 10px;
    font-weight: 14px;
}

button {
    border: none;
    outline: none;
    padding: 16px 50px;
    color: black;
    font-size: 16px;
    cursor: pointer;
    border-radius: 40px;
}

ul li {
    list-style: none;
    font-size: 17px;
    padding: 12px 8px 12px 50px;
    user-select: none;
    cursor: pointer;
    position: relative;
}

ul li::before {
    content: '';
    position: absolute;
    height: 28px;
    width: 28px;
    border-radius: 50%;
    background-image: url(prof.avif);
    background-size: cover;
    background-position: center;
    top: 12px;
    left: 8px;
}

ul li.checked {
    color: #555;
    text-decoration: line-through;
}

ul li.checked::before {
    background-image: url(smartwatch.png);
}

ul li span {
    position: absolute;
    right: 0;
    top: 5px;
    width: 40px;
    height: 40px;
    font-size: 22px;
    color: #555;
    line-height: 40px;
    text-align: center;
    border-radius: 50%;
}

ul li span:hover {
    background: #edeef0;
}
```
javascript
```
const inputBox = document.getElementById("input-box");
const listContainer = document.getElementById("list-container");
const allBtn = document.getElementById("all-btn");
const completedBtn = document.getElementById("completed-btn");
const clearBtn = document.getElementById("clear-btn");

function addTask() {
    if (inputBox.value === '') {
        alert("You must write something!");
    } else {
        let li = document.createElement("li");
        li.innerHTML = inputBox.value;
        listContainer.appendChild(li);
        let span = document.createElement("span");
        span.innerHTML = "\u00d7";
        li.appendChild(span);
    }
    inputBox.value = "";
    saveData();
}

listContainer.addEventListener("click", function(e) {
    if (e.target.tagName === "LI") {
        e.target.classList.toggle("checked");
        saveData();
    } else if (e.target.tagName === "SPAN") {
        e.target.parentElement.remove();
        saveData();
    }
}, false);

function saveData() {
    localStorage.setItem("data", listContainer.innerHTML);
}

function showTask() {
    listContainer.innerHTML = localStorage.getItem("data");
}

showTask();

function setActiveButton(button) {
    allBtn.classList.remove("active");
    activeBtn.classList.remove("active");
    completedBtn.classList.remove("active");
    button.classList.add("active");
}

allBtn.addEventListener("click", () => {
    setActiveButton(allBtn);
    const tasks = listContainer.getElementsByTagName("li");
    for (let task of tasks) {
        task.style.display = "block";
    }
});

activeBtn.addEventListener("click", () => {
    setActiveButton(activeBtn);
    const tasks = listContainer.getElementsByTagName("li");
    for (let task of tasks) {
        if (task.classList.contains("checked")) {
            task.style.display = "none";
        } else {
            task.style.display = "block";
        }
    }
});

completedBtn.addEventListener("click", () => {
    setActiveButton(completedBtn);
    const tasks = listContainer.getElementsByTagName("li");
    for (let task of tasks) {
        if (task.classList.contains("checked")) {
            task.style.display = "block";
        } else {
            task.style.display = "none";
        }
    }
});

clearBtn.addEventListener("click", () => {
    const tasks = listContainer.getElementsByClassName("checked");
    // Convert to an array to avoid issues with live HTMLCollection
    while(tasks.length > 0){
        tasks[0].remove();
    }
    saveData();
});
```


## OUTPUT
<img width="1919" height="1197" alt="image" src="https://github.com/user-attachments/assets/4d4faf80-593e-4f65-9df3-5210caff6367" />
<img width="1915" height="1199" alt="image" src="https://github.com/user-attachments/assets/b5d4c5ed-01e0-4663-bc2e-9a83c010e446" />



## RESULT
The program for creating To-do list using JavaScript is executed successfully.
