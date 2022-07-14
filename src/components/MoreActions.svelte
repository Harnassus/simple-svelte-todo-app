<script>

    import {createEventDispatcher} from 'svelte'
    const dispatch = createEventDispatcher();
    export let todos
    let completed = true;

    const checkAll = () => {
        dispatch('checkAll', completed)
        completed = !completed
    }
    const remove = () => {
        dispatch('removeCompleted')
    }
    $: completedTodos = todos.filter(t => t.completed).length
</script>

<div class="btn-group">
      <button disabled={todos.length === 0} type="button" class="btn btn__primary" on:click={checkAll}>{completed ? 'Check' : 'Uncheck'} all</button>
      <button disabled={completedTodos === 0} type="button" class="btn btn__primary" on:click={remove}>Remove completed</button>
</div>

<style>
 .btn-group{
        display: flex;
        justify-content: center;
        gap: 1em;
        margin-top: 2em;
    }
    .btn-group > button {
        padding: 0.5em;
        border-radius: 1em;
        border: none;
  }
</style>