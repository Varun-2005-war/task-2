<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Simple Web Page</title>

  <style>
    body {
      font-family: sans-serif;
      background-color: #f5f5f5;
      padding: 30px;
    }

    h1 {
      color: #333;
    }

    .main-layout {
      display: grid;
      grid-template-columns: 1fr;
      gap: 30px;
    }

    @media (min-width: 600px) {
      .main-layout {
        grid-template-columns: 1fr 1fr;
      }
    }

    .box {
      background: #fff;
      border-radius: 10px;
      padding: 20px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }

    form label {
      display: block;
      margin-top: 15px;
    }

    input[type="text"],
    input[type="email"] {
      width: 100%;
      padding: 10px;
      margin-top: 5px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }

    button {
      margin-top: 15px;
      padding: 10px;
      width: 100%;
      background: #007bff;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    button:hover {
      background: #0056b3;
    }

    ul {
      margin-top: 15px;
      padding-left: 20px;
    }

    ul li {
      margin-bottom: 10px;
      list-style-type: circle;
      cursor: pointer;
    }

    ul li:hover {
      text-decoration: line-through;
      color: red;
    }
  </style>
</head>
<body>

  <h1>Welcome</h1>

  <div class="main-layout">
    <div class="box">
      <h2>Contact Form</h2>
      <form id="contactForm">
        <label for="name">Your Name:</label>
        <input type="text" id="name" required />

        <label for="email">Your Email:</label>
        <input type="email" id="email" required />

        <button type="submit">Submit</button>
      </form>
    </div>

    <div class="box">
      <h2>To-Do List</h2>
      <input type="text" id="taskInput" placeholder="Add a new task..." />
      <button onclick="addTask()">Add Task</button>
      <ul id="taskList"></ul>
    </div>
  </div>

  <script>
    document.getElementById("contactForm").addEventListener("submit", function(e) {
      const email = document.getElementById("email").value;
      const emailRegex = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;

      if (!emailRegex.test(email)) {
        alert("Please enter a valid email address.");
        e.preventDefault();
      } else {
        alert("Form submitted successfully.");
      }
    });

    function addTask() {
      const taskInput = document.getElementById("taskInput");
      const taskText = taskInput.value.trim();

      if (taskText !== "") {
        const li = document.createElement("li");
        li.textContent = taskText;
        li.onclick = () => li.remove();
        document.getElementById("taskList").appendChild(li);
        taskInput.value = "";
      } else {
        alert("Task cannot be empty.");
      }
    }
  </script>

</body>
</html>
