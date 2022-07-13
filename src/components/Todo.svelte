<script>
  export let todo;
  import {createEventDispatcher} from 'svelte';
  const dispatch = createEventDispatcher();

  let editing = false;
  let name = todo.name;
  console.log(name)

  function update(updatedTodo) {
    todo = {...todo, ...updatedTodo}
    dispatch('update', todo)
    console.log(todo)
  }
  function onSave(){
    update({name: name});
    editing = false;
  }
  function onCancel(){
    name = todo.name;
    editing = false;
  }
  function onRemove() {
    dispatch('delete', todo)
  }
  function onEdit(){
    editing = true;
  }
  function onToggle() {
    update({completed: !todo.completed})
  }

</script>

<div class="todo">
    {#if (!editing)}
        <div class="todo-header">
        <input type="checkbox" class="todo-check" checked={todo.completed} id="todo-{todo.id}" on:click={onToggle}>
        <label for="todo-name" class="todo-name">{todo.name}</label>
        </div>
        <div class="todo-btn-group">
        <button on:click={onEdit}>Edit</button>
        <button class="danger" on:click={onRemove}>Delete</button>
        </div>
     {:else}
     <form on:submit|preventDefault={onSave} class="edit-form" on:keydown={e =>e.key=== 'Escape' && onCancel()}>
        <div class="form-group">
            <label for="todo-{todo.id}" class="todo-name">Rename '{todo.name}'</label>
            <input type="text" bind:value={name} id="todo-{todo.id}" autocomplete="off" class="edit-input"/>
        </div>
        <div class="btn-group">
         <button class="danger" on:click={onCancel} type="button">
            Cancel
         </button>
         <button class="" type="submit" disabled= {!name} on:click={onSave}>Save</button>
        </div>
     </form> 
    {/if}    
</div>

<style>
    .todo {
     display: flex;
      flex-direction: column;
      align-items: center;
      width: 100%;
      border: 2px solid black;
      border-radius: 1em;
      padding: 0.5em;
      margin: 1em;
      gap: 1em;
    }

    /* each todo component styles */
    .todo-header{
        display: flex;
        align-items: center;
        gap: 0.5em;
        margin: .5em;
    }
    .todo-header > input.todo-check{
        width: 2em;
        height: 2em;
    }
    .todo-header > label.todo-name{
        font-size: 1.3em;
    }

    .todo-btn-group {
        display: flex;
        gap: 1em;
    }
    .todo-btn-group > button {
        width: 100px;
        padding: 0.5em;
        border: 2px solid black;
        border-radius: 1em;
    }
    .danger{
        border: none;
        border-radius: none;
        background-color: rgb(253, 55, 55);
        color: white;
    }
    /* end of each todo component styles */

    /* end of each todo style */

    /* edit mode styles */
    .form-group {
        padding: 1em;
    }
    .todo-name{
        font-size: 1.2em;
        font-weight: bold;
    }
    .edit-input{
        font-size: 1em;
        width: 20em;
        padding: 0.5em;
        margin: 0.5em;
        border-radius: .5em;
    }
    .btn-group{
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 0.5em;
    }
    .btn-group > button{
        width: 100px;
        padding: 0.5em;
        border: 2px solid black;
        border-radius: 1em;
    }
</style>