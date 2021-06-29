<script>
    import TodoItem from './TodoItem.svelte';

	export let todo = '';
	export let todos = [
        { completed: false, text: 'Build something with Aurelia 2' },
        { completed: false, text: 'Buy milk' },
        { completed: false, text: 'Joes birthday present for this Saturday' },
        { completed: false, text: 'Take out the garbage' },
        { completed: false, text: 'Build something with Aurelia 2' },
        { completed: false, text: 'Buy milk' },
        { completed: false, text: 'Joes birthday present for this Saturday' },
        { completed: false, text: 'Take out the garbage' }
    ];

    function newTodo(event) {
        if (event.which === 13) {
            todos.unshift({ completed: false, text: todo });
            todo = '';
            todos = todos;
        }

        return true;
    }

    function deleteTodo(index) {
        todos.splice(index, 1);

        todos = todos;
    }
</script>

<div class="todo">
    <h1>Svelte Todo</h1>

    <div class="todo-container">
        <div class="todo-compose">
            <input type="text" bind:value={todo} on:keypress={newTodo} placeholder="What do you want to do today?">
        </div>

        <div class="todo-items">
            {#each todos as todo, i}
                <TodoItem {todo} {deleteTodo} index={i} on:deleteTodo={deleteTodo} />
            {/each}
        </div>
    </div>
</div>

<style>
.todo-container {
    background: white;
    border-radius: 8px;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
    display: grid;
    grid-template-rows: 60px 1fr;
    grid-column: 2;
    grid-row: 2;
    overflow: auto;
    margin-right: -18px;
    margin-left: -18px;
}

.todo-compose {
    align-items: stretch;
    box-shadow: 0 -1px 6px rgba(0, 0, 0, 0.19);
    border-bottom: 1px solid #e6e6e6;
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: 60px;
}

    .todo-compose button {
        color: #e6e6e6;
        justify-self: stretch;
        text-align: center;
    }

    .todo-compose input {
        border: none;
        border-bottom: 1px solid #e6e6e6;
        font-size: 18px;
        outline: none;
        padding: 15px;
    }

.todo-items {
    display: grid;
    grid-auto-columns: 1fr;
    grid-auto-rows: max-content;
    list-style-type: none;
    overflow: auto;
}

::placeholder {
    color: #e6e6e6;
    font-style: italic;
  }
</style>