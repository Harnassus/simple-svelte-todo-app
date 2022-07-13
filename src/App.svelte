<script>
import Todo from './components/Todos.svelte'
let todos = [
  { id: 1, name: 'Create a Svelte starter app', completed: true },
    { id: 2, name: 'Create your first component', completed: true },
    { id: 3, name: 'Complete the rest of the tutorial', completed: false }
]
let size = window.innerWidth;
</script>

<main>
{#if (size <= 500)}
 <Todo {todos}/>
{:else}
 <h1>Yikes! this site isn't available on Desktop</h1>
 {/if}
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }
  main{
    text-align: center;
  }

</style>
