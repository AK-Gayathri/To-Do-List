




































!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Modern To-Do List</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #f0f4f8;
      padding: 30px;
      display: flex;
      justify-content: center;
    }

    .todo-container {
      background: #ffffff;
      padding: 25px;
      border-radius: 12px;
      box-shadow: 0 4px 16px rgba(0,0,0,0.1);
      width: 100%;
      max-width: 500px;
    }

    h1 {
      text-align: center;
      color: #2c3e50;
      margin-bottom: 20px;
    }

    input, select {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 1rem;
    }  

    button {
      width: 100%;
      padding: 10px;
      margin-top: 15px;
      background-color: #3498db;
      color: white;
      border: none;
      border-radius: 8px;
      font-size: 1rem;
      cursor: pointer;
    }

    button:hover {
      background-color: #2980b9;
    }

    .task-card {
      background: #e8f8f5;
      margin-top: 15px;
      padding: 15px;
      border-left: 5px solid #1abc9c;
      border-radius: 10px;
    }

    .task-card.completed {
      text-decoration: line-through;
      background-color: #dfe6e9;
      opacity: 0.7;
    }

    .task-buttons {
      display: flex;
      justify-content: space-between;
      margin-top: 10px;
    }

    .complete-btn {
      background-color: #2ecc71;
      color: white;
      border: none;
      padding: 8px 12px;
      border-radius: 6px;
      cursor: pointer;
    }

    .delete-btn {
      background-color: #e74c3c;
      color: white;
      border: none;
      padding: 8px 12px;
      border-radius: 6px;
      cursor: pointer;
    }

    .complete-btn:hover {
      background-color: #27ae60;
    }}

    .delete-btn:hover {
      background-color: #c0392b;
    }
  </style>
</head>
<body>
  <div class="todo-container">
    <h1>Modern To-Do List</h1>
    <input type="text" id="taskInput" placeholder="Enter task" />
    <input type="date" id="dueDateInput" />
    <select id="categoryInput">
      <option value="" disabled selected>Select category</option>
      <option value="Work">Work</option>
      <option value="Personal">Personal</option>
      <option value="Urgent">Urgent</option>
      <option value="Others">Others</option>
    </select>
    <button onclick="addTask()">Add Task</button>

    <div id="taskList"></div>
  </div>

  <script>
    function addTask() {
      const taskInput = document.getElementById("taskInput");
      const dueDateInput = document.getElementById("dueDateInput");
      const categoryInput = document.getElementById("categoryInput");

      const task = taskInput.value.trim();
      const dueDate = dueDateInput.value;
      const category = categoryInput.value;

      if (!task || !dueDate || !category) {
        alert("Please fill all fields.");
        return;
      }

      const taskCard = document.createElement("div");
      taskCard.className = "task-card";

      taskCard.innerHTML = `
        <strong>${task}</strong><br>
        Due: ${dueDate}<br>
        Category: ${category}
        <div class="task-buttons">
          <button class="complete-btn" onclick="toggleComplete(this)">Complete</button>
          <button class="delete-btn" onclick="deleteTask(this)">Delete</button>
        </div>
      `;

      document.getElementById("taskList").appendChild(taskCard);

      // Clear inputs
      taskInput.value = "";
      dueDateInput.value = "";
      categoryInput.selectedIndex = 0;
    }

    function deleteTask(button) {
      const taskCard = button.closest(".task-card");
      taskCard.remove();
    }

    function toggleComplete(button) {
      const taskCard = button.closest(".task-card");
      taskCard.classList.toggle("completed");
    }
  </script>
</body>
</html>


