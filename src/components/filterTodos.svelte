<script>
    export let filter = 'all';
    export let onclick = (clicked) => {}
    $: onclick(filter);
</script>

<div class="filter-btns">
    <button class="filter-btn" class:active={filter === 'all'} aria-pressed={filter === 'all'} on:click={() => filter = 'all'}>
      All
    </button>
    <button class="filter-btn" class:active ={filter === 'active'} on:click={() => filter = 'active'} aria-pressed={filter === 'active'}>
     Active
    </button>
    <button class="filter-btn" class:active ={filter === 'completed'} on:click={() => filter = 'completed'} aria-pressed={filter === 'completed'}>
     Completed
    </button>
</div>

<style>
    /* style for filetring todo by their current state */
    .filter-btns{
        display: flex;
        width: 100%;
        justify-content: center;
        gap: 1em;
    }
    .filter-btn{
    padding: 0.8rem 1rem 0.7rem;
    cursor: pointer;
    text-transform: capitalize;
    border-radius: 1em;
    border: none;
    }
    .filter-btn:hover{
        width: 8em;
    }
    .active{
        background-color: rgb(57, 174, 224);
        color: white;
    }
 /* end */
</style>