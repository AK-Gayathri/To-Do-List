# To-Do-List
!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Modern To-Do List</title>
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      font-family: 'Segoe UI', sans-serif;
      background: #e0f7fa;
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: flex-start;
      height: 100vh;
    }

    .todo-container {
      background: #ffffff;
      margin-top: 40px;
      padding: 30px 40px;
      border-radius: 20px;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
      width: 100%;
      max-width: 450px;
    }

    h1 {
      text-align: center;
      color: #00796b;
      margin-bottom: 20px;
    }

    .input-section {
      display: flex;
      flex-direction: column;
      gap: 10px;
      margin-bottom: 20px;
    }

    input, select {
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 1rem;
    }

    button {
      padding: 10px;
      background-color: #00796b;
      color: white;
      border: none;
      border-radius: 8px;
      font-size: 1rem;
      cursor: pointer;
      transition: background 0.3s;
    }

    button:hover {
      background-color: #004d40;
    }

    .task-card {
      background: #f1f8e9;
      padding: 15px;
      margin-bottom: 15px;
      border-left: 5px solid #00796b;
      border-radius: 10px;
      position: relative;
    }

    .task-card.completed {
      opacity: 0.6;
      text-decoration: line-through;
    }

    .task-info {
      display: flex;
      justify-content: space-between;
      flex-wrap: wrap;
    }

    .task-buttons {
      margin-top: 10px;
      display: flex;
      justify-content: flex-end;
      gap: 10px;
    }

    .task-buttons button {
      font-size: 0.9rem;
      padding: 5px 10px;
      border-radius: 5px;
    }

    .delete-btn {
      background: #e53935;
    }

    .complete-btn {
      background: #43a047;
    }

    .category {
      font-style: italic;
      font-size: 0.9rem;
      color: #555;
    }
  </style>
</head>
<body>
  <div class="todo-container">
    <h1>Modern To-Do List</h1>
    <div class="input-section">
      <input type="text" id="taskInput" placeholder="Enter task..." />
      <input type="date" id="dueDateInput" />
      <select id="categoryInput">
        <option value="" disabled selected>Select category</option>
        <option value="Work">Work</option>
        <option value="Personal">Personal</option>
        <option value="Urgent">Urgent</option>
        <option value="Others">Others</option>
      </select>
      <button onclick="addTask()">Add Task</button>
    </div>
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
        <div class="task-info">
          <div><strong>${task}</strong></div>
          <div><small>Due: ${dueDate}</small></div>
          <div class="category">Category: ${category}</div>
        </div>
        <div class="task-buttons">
          <button class="complete-btn" onclick="toggleComplete(this)">Complete</button>
          <button class="delete-btn" onclick="deleteTask(this)">Delete</button>
        </div>
      `;

      document.getElementById("taskList").appendChild(taskCard);

      // Clear input fields
      taskInput.value = "";
      dueDateInput.value = "";
      categoryInput.selectedIndex = 0;
    }

    function deleteTask(btn) {
      btn.closest(".task-card").remove();
    }

    function toggleComplete(btn) {
      const card = btn.closest(".task-card");
      card.classList.toggle("completed");
    }
  </script>
</body>
</html>


