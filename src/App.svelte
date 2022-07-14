<script>
import Todo from './components/Todos.svelte'
let todos = []
let size = window.innerWidth;
</script>

<main>
{#if (size <= 500)}
 <Todo {todos}/>
{:else}
 <h1>Yikes! this site is only available on mobile devices</h1>
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
