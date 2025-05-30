<!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>To-Do List</title>
  <style>
    body {
      font-family: sans-serif;
      background: #f2f2f2;
      padding: 40px;
      max-width: 600px;
      margin: auto;
    }
    h1 {
      text-align: center;
    }
    input, button {
      padding: 10px;
      font-size: 16px;
    }
    #new-task {
      width: 70%;
      margin-right: 10px;
    }
    ul {
      list-style: none;
      padding: 0;
    }
    li {
      background: white;
      padding: 10px;
      margin: 10px 0;
      border-radius: 5px;
      display: flex;
      justify-content: space-between;
    }
    .done {
      text-decoration: line-through;
      color: gray;
    }
  </style>
</head>
<body>
  <h1>La mia To-Do List</h1>
  <div>
    <input type="text" id="new-task" placeholder="Scrivi un'attività..." />
    <button onclick="addTask()">Aggiungi</button>
  </div>
  <ul id="task-list"></ul>

  <script>
    function addTask() {
      const taskText = document.getElementById("new-task").value;
      if (taskText === "") return;

      const li = document.createElement("li");
      li.innerHTML = `
        <span onclick="toggleDone(this)">${taskText}</span>
        <button onclick="deleteTask(this)">❌</button>
      `;
      document.getElementById("task-list").appendChild(li);
      document.getElementById("new-task").value = "";
    }

    function deleteTask(button) {
      button.parentElement.remove();
    }

    function toggleDone(span) {
      span.classList.toggle("done");
    }
  </script>
</body>
</html>
