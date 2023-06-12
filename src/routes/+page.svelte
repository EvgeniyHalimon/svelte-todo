<svelte:head>
    <link rel="stylesheet" href="https://unpkg.com/@picocss/pico@latest/css/pico.min.css">
</svelte:head>

<script>
	import TodoItem from "../components/TodoItem.svelte";

    let toDoList = []; 
    let textInput = "";

    function addToDo() {
        toDoList = [...toDoList, { content: textInput, checked: false }]
        textInput = "";
    }
</script>

<div style="margin: 0 auto; padding: 20px; width: 700px;">
    <h2 style="text-align: center;">ToDo List</h2>
    <p>Enter your ToDo here</p>
    <div style="display: flex; gap: 10px;">
        <input type="text" bind:value={textInput}>
        <button style="width: 200px;" on:click={addToDo}>Add</button>
    </div>
</div>

{#each toDoList as toDo, i}
    <TodoItem toDoList={toDoList} i={i}/>
{/each}