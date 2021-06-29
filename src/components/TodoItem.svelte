<script>
    export let todo;
    export let index;
    export let deleteTodo;
</script>

<div class="todo-item { todo.completed ? 'completed' : '' }">
    <input type="checkbox" bind:checked={todo.completed}>
    <p contenteditable="true" spellcheck="false">{ todo.text }</p>
    <button type="button" on:click={deleteTodo(index)}>x</button>
</div>

<style>
.todo-item {
    align-items: center;
    border-bottom: 1px solid #ededed;
    display: grid;
    grid-template-columns: 50px 450px 50px;
    word-wrap: break-word;
}

.todo-item input[type="checkbox"] {
    height: 25px;
    margin-left: 15px;
    width: 25px;
}

.todo-item.completed {
    color: #D9D9DD;
    text-decoration: line-through;
}

.todo-item p {
    box-shadow: none;
    font-size: 18px;
    outline: none;
    padding: 18px 0;
}

.todo-item p:focus {
    font-weight: bold;
}

.todo-item button {
    color: red;
    cursor: pointer;
    font-size: 24px;
    justify-self: end;
    visibility: hidden;
}

.todo-item:hover button {
    visibility: visible;
}
</style>