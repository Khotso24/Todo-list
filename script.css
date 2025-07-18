let todos = JSON.parse(localStorage.getItem("todos")) || [];

function addTodo() {
  const text = document.getElementById("todo-text").value;
  const date = document.getElementById("todo-date").value;
  const priority = document.getElementById("todo-priority").value;
  const tags = document.getElementById("todo-tags").value.split(',').map(t => t.trim());

  if (!text) return;

  const todo = {
    id: Date.now(),
    text,
    date,
    priority,
    tags
  };

  todos.push(todo);
  saveAndRender();
}

function deleteTodo(id) {
  todos = todos.filter(todo => todo.id !== id);
  saveAndRender();
}

function saveAndRender() {
  localStorage.setItem("todos", JSON.stringify(todos));
  renderTodos();
}

function renderTodos(filtered = todos) {
  const list = document.getElementById("todo-list");
  list.innerHTML = "";

  filtered.forEach(todo => {
    const li = document.createElement("li");
    li.className = todo.priority;

    li.innerHTML = `
      <strong>${todo.text}</strong><br/>
      <small>Due: ${todo.date || "No due date"} | Priority: ${todo.priority}</small><br/>
      <div class="tags">Tags: ${todo.tags.join(', ')}</div>
      <button onclick="deleteTodo(${todo.id})">❌</button>
    `;

    list.appendChild(li);
  });
}

function filterTodos() {
  const query = document.getElementById("search-bar").value.toLowerCase();
  const filtered = todos.filter(todo =>
    todo.text.toLowerCase().includes(query) ||
    todo.tags.some(tag => tag.toLowerCase().includes(query))
  );
  renderTodos(filtered);
}

function sortTodos() {
  const sortBy = document.getElementById("sort-by").value;
  if (sortBy === "date") {
    todos.sort((a, b) => new Date(a.date) - new Date(b.date));
  } else if (sortBy === "priority") {
    const order = { high: 1, medium: 2, low: 3 };
    todos.sort((a, b) => order[a.priority] - order[b.priority]);
  }
  saveAndRender();
}

// Initialize
renderTodos();
