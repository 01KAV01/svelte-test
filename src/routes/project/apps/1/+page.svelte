<script>

    import Icon from "./Icon.svelte";
    
        let newItem = "";
        export let todoList = []; 
    
        function add() {
            if (newItem !== "") {
                todoList = [
                    ...todoList,
                    {
                        задача: newItem,
                        completed: false, 
                    },
                ];
                newItem = "";
            }
        }
    
        function remove(index) {
            todoList = todoList.filter((_, i) => i !== index);
        }
    
        function complete(index) {
            todoList = todoList.map((item, i) => i === index ? {...item, completed: !item.completed} : item);
        }
        
    </script>
    
    <main>
        <h1>Список задач</h1>
        <form on:submit|preventDefault={add}>
            <input bind:value={newItem} placeholder="Enter to-do" />
            <button class="add-todo" on:click={add}><span>+</span></button>
        </form>
        <div class="todos">
            {#each todoList as item, index }
                <div class="todo" class:completed={item.completed}>
                    <span class="todo_text">{item.задача}</span>
                    <div class="todo_buttons">
                        <button class="complete" on:click={() => complete(index)}>
                            <Icon name="check-mark" />
                        </button>
                        <button class="delete" on:click={() => remove(index)}>
                            <Icon name="delete" />
                        </button>
                    </div>
                </div>
            {/each}
        </div>
    </main>
    
    <style>
    
    
    
    :root {
        --primary-color: #3498db;
        --secondary-color: #2ecc71;
        --text-color: #333;
        --background-color: #f5f5f5;
        --border-color: #e7e7e7;
    }
    
    body {
        font-family: 'Roboto', sans-serif; /* Пример современного шрифта */
        background-color: var(--background-color);
        color: var(--text-color);
    }
    
    h1 {
        text-align: center;
        font-size: 2rem;
        margin: 2em 0;
        color: var(--primary-color);
    }
    
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
        min-height: 100%;
        padding: 5vmin;
        box-sizing: border-box;
        background: var(--background-color);
    }
    
    form {
        width: 100%;
        max-width: 500px;
        display: flex;
        align-items: center;
        margin-bottom: 1em;
        padding: 10px;
        border-radius: 5px;
        box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    }
    
    input {
        flex-grow: 1;
        width: 0;
        border: none;
        border-bottom: 2px solid var(--border-color);
        background: transparent;
        box-shadow: none;
        font-size: 1.2rem;
        margin: 0;
        outline: none;
        padding: 10px;
    }
    
    button {
        background-color: var(--secondary-color);
        color: white;
        border: none;
        padding: 15px 20px;
        margin-left: 10px;
        cursor: pointer;
        border-radius: 5px;
        transition: background-color 0.3s ease;
    }
    
    button:hover {
        background-color: #27ae60;
    }
    
    button.delete,
    button.delete:hover{
    background-image: url(/src/components/delete.jpg);
    background-size: cover;
    background-position: center;
    transition: filter 0.3s ease;
    }
    
    button.delete:hover{
    
        filter: brightness(0.5);
    }
    
    
    
    button.complete,
    button.complete:hover{
    background-image: url(/src/components/check-mark.jpg);
    background-size: cover;
    background-position: center;
    transition: filter 0.3s ease;
    }
    
    button.complete:hover{
        filter: brightness(0.5); 
    }
    
    .todo {
        display: flex;
        padding: 20px;
        border-radius: 20px;
        box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
        background-color: var(--background-color);
        margin-top: 1rem;
        font-size: 1.2rem;
        justify-content: space-between;
        align-items: center;
        transition: background-color 0.3s ease;
    }
    
    .todo.completed {
        background-color: #e6e6e6;
        color: #999;
    }
    
    .todo.completed .todo_text {
        text-decoration: line-through;
    }
    
    .todo.completed button {
        color: silver;
    }
    
    .todos {
        width: 100%;
        max-width: 500px;
        margin-top: 20px;
    }
    
    </style>
    