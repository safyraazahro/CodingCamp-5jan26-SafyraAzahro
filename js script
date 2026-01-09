// Temporary Storage for Todo Items
let todos = [];
let currentFilter = 'all';

// Function to Add Todo Item
function addTodo() {
    const todoInput = document.getElementById('todo-input');
    const todoDate = document.getElementById('todo-date');

    console.log(todoInput.value);
    console.log(todoInput.value);

    if (todoInput.value === '' || todoDate.value === '') {
        alert('Please fill in both the todo item and the date.');
    } else {
        const newTodo = {
            task: todoInput.value,
            date: todoDate.value,
            done: false
        };

        // Add the new todo to the todos array
        todos.push(newTodo);

        renderTodos();

        // Clear input fields
        todoInput.value = '';
        todoDate.value = '';
    }
}

/// Function to render todo items to the DOM
function renderTodos() {
    const todoList = document.getElementById('todo-list');

    // Clear existing list
    todoList.innerHTML = '';

    // Filter todos based on current filter
    let filtered = todos;
    if (currentFilter === 'pending') {
        filtered = todos.filter(t => !t.done);
    } else if (currentFilter === 'completed') {
        filtered = todos.filter(t => t.done);
    }

    // Show message if no todos
    if (filtered.length === 0) {
        todoList.innerHTML = '<li>No todos available</li>';
        return;
    }

    // Render each todo item
    filtered.forEach((todo, idx) => {
        const realIdx = todos.indexOf(todo);
        const checked = todo.done ? 'checked' : '';
        const textClass = todo.done ? 'line-through text-gray-400' : '';

        todoList.innerHTML += `
        <li class="py-2">
            <label class="flex items-center gap-2">
                <input type="checkbox" ${checked} onchange="toggleTodo(${realIdx})" />
                <span class="text-2xl ${textClass}">${todo.task} <span class="text-sm text-gray-500">(${todo.date})</span></span>
            </label>
            <hr />
        </li>`;
    });
}

// Function to Remove All Todo Items
function removeAllTodo() {
    todos = [];

    // Re-Render the empty list
    renderTodos();
}

// Function to Toggle Filter
function filterTodo() {
    const filterBtn = document.getElementById('filter-btn');
    
    // Cycle through filter states
    if (currentFilter === 'all') {
        currentFilter = 'pending';
        filterBtn.textContent = 'Filter: Pending';
    } else if (currentFilter === 'pending') {
        currentFilter = 'completed';
        filterBtn.textContent = 'Filter: Completed';
    } else {
        currentFilter = 'all';
        filterBtn.textContent = 'Filter Todos';
    }
    
    renderTodos();
}

// Function to Toggle Todo Done Status
function toggleTodo(index) {
    if (todos[index]) {
        todos[index].done = !todos[index].done;
        renderTodos();
    }
}
