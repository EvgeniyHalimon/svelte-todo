<script>
    export let toDoList;
    export let i;
    let isEditing = false;

    function setEditing(editing) {
        isEditing = editing; 
    }

    function deleteTodo(i) {
        toDoList.splice(i, 1);
        toDoList = toDoList; 
    }
</script>

<div style="display: flex; align-items: baseline; width: 700px; padding: 20px; margin: 0 auto; gap: 10px;">
    {#if isEditing}
        <input type="text" bind:value={toDoList[i].content}>
    {:else}
        <input type="checkbox" bind:checked={toDoList[i].checked}>
        <h4 style="flex-grow: 1">{toDoList[i].content}</h4>
    {/if}
    <div style="display: flex; gap: 10px;">
        {#if isEditing}
            <button on:click={() => setEditing(false)}>Save</button>
        {:else}
            <button on:click={() => setEditing(true)}>Edit</button>
        {/if}
        <button on:click={() => deleteTodo(i)}>Delete</button>
    </div>
</div>