# full-stack-development-
<!DOCTYPE html>
<html>
  <head>
    <title>Sign Up</title>
    <link rel="stylesheet" href="style2.css" />
    <script defer src="signup.js"></script>
  </head>
  <body>
    <div class="header">
      <h3 class="title">Liste des tâches</h3>
    </div>
    <div class="auth-container">
      <h2>Sign Up</h2>
      <form id="signup-form">
        <input type="Name" id="signup-name" placeholder="Name" required />
        <input type="email" id="signup-email" placeholder="Email" required />
        <input type="password" id="signup-password" placeholder="Password" required />
        <button class="add-btn type="submit">Sign Up</button>
      </form>
      <p>
        Already have an account? <a href="signin.html">Sign In</a>
      </p>
    </div>
  </body>
</html>

•	signup.js
document.getElementById('signup-form').addEventListener('submit', function (e) {
    e.preventDefault();
    username = document.getElementById('signup-password').value;
    const Name = document.getElementById('signup-name').value;
    const email = document.getElementById('signup-email').value;
    const password = document.getElementById('signup-password').value;
 
    // Store the credentials in localStorage
    localStorage.setItem('email', email);
    localStorage.setItem('password', password);
    localStorage.setItem('Name',Name);
 
    alert('Account created successfully!');
    window.location.href = 'signin.html'; // Redirect to the sign-in page
  });

•	signin.html
<!DOCTYPE html>
<html>
  <head>
    <title>Sign In</title>
    <link rel="stylesheet" href="style2.css" />
    <script defer src="signin.js"></script>
  </head>
  <body>
    <div class="header">
      <h3 class="title">Liste des tâches</h3>
    </div>
    <div class="auth-container">
      <h2>Sign In</h2>
      <form id="signin-form">
        <input type="email" id="signin-email" placeholder="Email" required />
        <input type="password" id="signin-password" placeholder="Password" required />
        <button type="submit">Sign In</button>
      </form>
      <p>
        Don't have an account? <a href="signup.html">Sign Up</a>
      </p>
    </div>
  </body>
</html>

•	signin.js
document.getElementById('signin-form').addEventListener('submit', function (e) {
  e.preventDefault();

  const email = document.getElementById('signin-email').value;
  const password = document.getElementById('signin-password').value;

  // Get stored credentials
  const storedEmail = localStorage.getItem('email');
  const storedPassword = localStorage.getItem('password');
  // Check if entered credentials match the stored ones
  if (email === storedEmail && password === storedPassword) {
    window.location.href = 'index.html'; // Redirect to the to-do list page
  } else {
    alert('Incorrect email or password');
  }
});

•	style.css
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body {
  background: url('bgr.jpg') no-repeat center center fixed;
  background-size: cover;
  font-family: 'Poppins', sans-serif;
  color: #333;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 20px;
  background-color: rgba(157, 66, 223, 0.8);
  color: white;
  position: absolute;
  top: 0;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}

.title {
  font-size: 3.5rem;
  font-weight: bold;
  text-align: center;
  width: 100%;
}

.profile {
  width: 60px;
  height: 60px;
  background: url('prof.jpg') no-repeat center center;
  background-size: cover;
  border-radius: 50%;
  position: absolute;
  top: 20px;
  right: 20px;
  border: 4px solid white;
}

.container {
  width: 100%;
  max-width: 600px;
  margin-top: 6rem;
  background-color: rgba(255, 255, 255, 0.9);
  padding: 2rem;
  border-radius: 15px;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
   /* Align content to the right */
  margin-left: auto;
}

form {
  display: flex;
  justify-content: space-between;
  margin-bottom: 1.5rem;
}

#task-input {
  flex: 1;
  padding: 15px;
  border: 2px solid #ccc;
  border-radius: 10px;
  font-size: 1.2rem;
}

.add-btn {
  background-color: #6a0dad;
  color: white;
  border: none;
  padding: 15px 20px;
  font-size: 1.2rem;
  margin-left: 10px;
  border-radius: 10px;
  cursor: pointer;
  transition: background-color 0.3s, transform 0.3s;
}

.add-btn:hover {
  background-color: #9246d8;
  transform: scale(1.05);
}

.task-items {
  list-style: none;
  padding: 0;
  margin: 0;
  max-height: 400px;
  overflow-y: auto;
}

.task {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
  background-color: #f8f8f8;
  border: 2px solid #ddd;
  margin-bottom: 10px;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: transform 0.2s;
}

.task:hover {
  transform: scale(1.02);
}

.task input {
  border: none;
  background-color: transparent;
  font-size: 1.2rem;
  width: 80%;
}

.task input:disabled {
  color: #333;
}

.edit-btn, .delete-btn {
  background-color: #6a0dad;
  color: white;
  border: none;
  padding: 10px 15px;
  font-size: 1rem;
  margin-left: 5px;
  border-radius: 10px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.edit-btn:hover, .delete-btn:hover {
  background-color: #dd0836;
}

#search {
  width: 100%;
  padding: 15px;
  border: 2px solid #ccc;
  border-radius: 10px;
  margin-bottom: 20px;
  font-size: 1.2rem;
}

.clear-tasks {
  background-color: #6a0dad;
  color: white;
  border: none;
  padding: 15px;
  width: 100%;
  font-size: 1.2rem;
  border-radius: 10px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.clear-tasks:hover {
  background-color: #dd0836;
}

.err {
  display: none;
  background-color: rgb(234, 175, 175);
  color: red;
  padding: 10px;
  margin-bottom: 10px;
  border-radius: 5px;
  text-align: center;
}

/* Scrollbar styling */
.task-items::-webkit-scrollbar {
  width: 8px;
}

.task-items::-webkit-scrollbar-thumb {
  background-color: #6a0dad;
  border-radius: 10px;
}

.task-items::-webkit-scrollbar-track {
  background-color: #f0f0f0;
}

.left-image {
  position: absolute;
  left: 10px;
  top: 50%;
  transform: translateY(-50%);
  width: 150px; /* Adjust width as needed */
  height: auto;
  border-radius: 10px; /* Optional: To give the image rounded corners */
}

.main-content {
  display: flex;
  align-items: center;
  justify-content: flex-start; /* Align image to the left */
  width: 100%;
}

.side-image {
  width: 40%; /* Image width remains the same */
  height: auto;
  margin: 0; /* No spacing between image and task container */
  padding-left: 80px; /* Increased padding to 60px */
  border-radius: 10px;
  transition: transform 0.3s ease;
}

.side-image:hover {
  transform: scale(1.4); /* Stronger zoom effect on hover */
}

.container {
  width: 400%; /* Adjusted container width to balance image size */
  max-width: 800px;
  margin-top: 6rem;
  background-color: rgba(255, 255, 255, 0.9);
  padding: 2rem;
  border-radius: 15px;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
  margin-left: 0;
}

.completed {
  text-decoration: line-through;
  color: #888;
}

.complete-btn {
  background-color: #28a745;
  color: white;
  border: none;
  padding: 10px 15px;
  font-size: 1rem;
  margin-left: 5px;
  border-radius: 10px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.complete-btn:hover {
  background-color: #218838;
}

•	index.html
<!DOCTYPE html>
<html>
  <head>
    <title>Liste des tâches</title>
    <script defer src="app.js"></script>
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <div class="header">
      <h3 class="title">Liste des tâches</h3>
      <div class="profile"></div>
    </div>
   
    <div class="main-content">
      <img class="side-image" src="img2.webp" alt="Task Image" />
     
      <div class="container">
        <h6 class="title">The Task Board</h6>
        <p class="err">Please enter a task</p>
        <form>
          <input id="task-input" type="text" placeholder="Add a task" />
          <button class="add-btn">Add task</button>
        </form>
        <div class="sort-options">
          <select id="sort-tasks">
            <option value="asc">completed</option>
            <option value="des">pending</option>
          </select>
        </div>
        <input type="text" id="search" placeholder="Search a task" />
        <ul class="task-items"></ul>
        <button class="clear-tasks">Clear All Tasks</button>
      </div>
    </div>
  </body>
</html>

•	app.js
const taskInput = document.getElementById("task-input");
const addBtn = document.querySelector(".add-btn");
const taskList = document.querySelector(".task-items");
const clearAll = document.querySelector(".clear-tasks");
const searchInput = document.querySelector("#search");
const sortSelect = document.getElementById("sort-tasks");

addBtn.addEventListener("click", function (e) {
  e.preventDefault();
  // get the value from the input filed trim
  const taskText = taskInput.value.trim();
  // check id the value of the input is not empty
  if (taskInput.value !== "") {
    // create li
    const newLi = document.createElement("li");
    newLi.className = "task";
    newLi.style.margin = ".5rem 0rem";

    // create an input field
    const task = document.createElement("input");
    task.disabled = true;
    task.type = "text";
    task.className = "taskDisabled";
    // make the value of the input to be our text
    task.value = taskText;
    // create a button
    const deleteBtn = document.createElement("button");
    deleteBtn.className = "delete-btn";
    deleteBtn.innerText = "Delete";

    // create an edit button
    const editBtn = document.createElement("button");
    editBtn.className = "edit-btn";
    editBtn.innerText = "Edit";

    //create complete button
    const completeBtn = document.createElement("button");
    completeBtn.className = "complete-btn";
    completeBtn.innerText = "Complete";

    // append the input text
    newLi.appendChild(task);
    newLi.appendChild(deleteBtn);
    newLi.appendChild(editBtn);
    newLi.appendChild(completeBtn);
    taskList.appendChild(newLi);

    taskInput.value = "";
  } else {
    const err = document.querySelector(".err");
    // err.style.background = "blue";
    err.style.display = "block";
    setTimeout(() => {
      err.style.display = "none";
    }, 2000);
  }
});

taskList.addEventListener("click", (e) => {
  //  get the paren of the button
  // check if the target is the delete button
  if (e.target.classList.contains("delete-btn")) {
    // remove the parent
    e.target.parentElement.remove();
    sortTasks();
  }
});
// edit
taskList.addEventListener("click", (e) => {
  if (e.target.classList.contains("edit-btn")) {
    console.log(e.target.parentElement);
    const input = e.target.parentElement.querySelector('input[type="text"]');
    input.disabled = !input.disabled;
    if (!input.disabled) {
      input.focus();
    }
  }


if (e.target.classList.contains("complete-btn")) {
  const task = e.target.parentElement.querySelector(".taskDisabled");
  task.classList.toggle("completed");
  e.target.innerText = task.classList.contains("completed") ? "Undo" : "Complete";
}
});

clearAll.addEventListener("click", function (e) {
  e.preventDefault();
  taskList.innerHTML = "";
});

// Add an event listener to the search input field
searchInput.addEventListener("keyup", (e) => {
  e.preventDefault();
  let searchedWord = e.target.value.toLowerCase();

  const taskItems = document.querySelectorAll(".task");
  taskItems.forEach((taskItem) => {
    let taskText = taskItem.querySelector(".taskDisabled").value.toLowerCase();

    if (taskText.indexOf(searchedWord) !== -1) {
      taskItem.style.display = "block";
    } else {
      taskItem.style.display = "none";
    }
  });
});

// Sorting function
sortSelect.addEventListener("change", () => {
  sortTasks();
});

function sortTasks() {
  const taskItems = Array.from(taskList.children);
  const sortOrder = sortSelect.value;

  taskItems.sort((a, b) => {
    const taskA = a.querySelector(".taskDisabled").value.toLowerCase();
    const taskB = b.querySelector(".taskDisabled").value.toLowerCase();

    if (sortOrder === "asc") {
      return taskA.localeCompare(taskB);
    } else {
      return taskB.localeCompare(taskA);
    }
  });

  taskList.innerHTML = "";
  taskItems.forEach((item) => taskList.appendChild(item));
}



document.addEventListener("DOMContentLoaded", () => {
  const sortTasksSelect = document.getElementById("sort-tasks");
  const taskItemsList = document.querySelector(".task-items");

  // Function to display tasks
  function displayTasks(filteredTasks) {
    taskItemsList.innerHTML = "";
    filteredTasks.forEach((task, index) => {
      const li = document.createElement("li");

      // Add a checkbox to mark task as completed/pending
      const checkbox = document.createElement("input");
      checkbox.type = "checkbox";
      checkbox.checked = task.completed;
      checkbox.addEventListener("change", () => toggleTaskStatus(index));

      li.appendChild(checkbox);
      li.appendChild(document.createTextNode(task.task));
      taskItemsList.appendChild(li);
    });
  }

  // Function to sort tasks based on selection
  function sortTasks() {
    const sortOption = sortTasksSelect.value;

    let filteredTasks;
    if (sortOption === "asc") {
      filteredTasks = tasks.filter(task => task.completed); // Show completed tasks
    } else if (sortOption === "des") {
      filteredTasks = tasks.filter(task => !task.completed); // Show pending tasks
    }

    displayTasks(filteredTasks);
  }

  // Toggle the completion status of a task
  function toggleTaskStatus(index) {
    tasks[index].completed = !tasks[index].completed;
    sortTasks(); // Update the task list after changing the status
  }

  // Event listener for sorting
  sortTasksSelect.addEventListener("change", sortTasks);

  // Initially display all tasks (or you can choose to display only pending/completed)
  displayTasks(tasks);
});  
sortSelect.addEventListener("change", () => {
  sortTasks();
});

function sortTasks() {
  const taskItems = Array.from(taskList.children);
  const sortOrder = sortSelect.value;

  taskItems.forEach((task) => {
    const taskInput = task.querySelector(".taskDisabled");
   
    // For completed tasks
    if (sortOrder === "asc" && taskInput.classList.contains("completed")) {
      task.style.display = "flex"; // Show completed tasks
    }
    // For pending tasks
    else if (sortOrder === "des" && !taskInput.classList.contains("completed")) {
      task.style.display = "flex"; // Show pending tasks
    }
    // Hide other tasks
    else {
      task.style.display = "none";
    }
  });
}         

•	style2.css
/* General Reset */
* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }
 
  /* Body styling */
  body {
    background: url('bgr.jpg') no-repeat center center fixed;
    background-size: cover;
    font-family: 'Poppins', sans-serif;
    color: #333;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
    text-align: center;
  }
 
  /* Title Styling */
  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    padding: 20px;
    background-color: rgba(106, 13, 173, 0.8);
    color: white;
    position: absolute;
    top: 0;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
  }
  .title {
    font-size: 3.5rem;
    font-weight: bold;
    text-align: center;
    width: 100%;
  }
  /* Sign-In and Sign-Up Container Styling */
  .auth-container {
    width: 100%;
    max-width: 400px;
    background-color: rgba(255, 255, 255, 0.9);
    padding: 2rem;
    border-radius: 15px;
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
    margin-top: 2rem;
    text-align: center;
  }
 
  /* Form Elements Styling */
  input {
    width: 100%;
    padding: 15px;
    margin: 10px 0;
    border-radius: 10px;
    border: 2px solid #ccc;
    font-size: 1.2rem;
  }
 
  button {
    width: 100%;
    padding: 15px;
    background-color: #6a0dad;
    color: white;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition: background-color 0.3s, transform 0.3s;
  }
 
  button:hover {
    background-color: #9246d8;
    transform: scale(1.05);
  }
 
  /* Link Styling */
  p {
    margin-top: 20px;
  }
 
  a {
    color: #6a0dad;
    text-decoration: none;
  }
 
  a:hover {
    text-decoration: underline;
  }

