<script>

  export let todos = [];
  import Filtered from './filterTodos.svelte';
  import Todo from './Todo.svelte';

  $: totalTodos = todos.length
  $: completedTodos = todos.filter(todo => todo.completed).length;
  $: newTodoName = '';
  let newTodoId
  $: {
    if(totalTodos === 0 ){
      newTodoId = 1;
    }else newTodoId = Math.max(...todos.map(todo => todo.id)) + 1;
  }


    const removeTodo = (todo) => {
      todos = todos.filter(t => t.id !== todo.id)
    }
    function addTodo() {
      newTodoName = newTodoName.trim();
      if (newTodoName){
        todos = [...todos, { id: newTodoId, name: newTodoName, completed: false}];
        newTodoName = ''
        console.log(todos)
      }else alert('write something')
    }

   let filter 
   const filterTodos = (filter, todos) => 
   filter === 'active' ? todos.filter(todo => !todo.completed ):
   filter === 'completed' ? todos.filter(todo => todo.completed) :
   todos;
      
</script>

  <main>
    <form class="create" on:submit|preventDefault={addTodo}>
      <h2 class="create-label">
          What needs to be done?
      </h2>
      <input type="text" id="todo-0" autocomplete="off" bind:value={newTodoName} class="create-input"/><br/>
      <button type="button" on:click={() => addTodo()} class="create-btn">
        Add
      </button>
    </form>

      <Filtered bind:filter={filter}/> 

      <h2>{completedTodos} out of {totalTodos} items completed</h2>
      <div class="todo-list">
          {#each filterTodos(filter, todos) as todo (todo.id)}
              <Todo {todo} on:delete={e => removeTodo(e.detail)}/>
              {:else}
              <p>Nothing to do</p>
          {/each}
      </div>

      <hr />
    
    <div class="btn-group">
      <button type="button" class="btn btn__primary">Check all</button>
      <button type="button" class="btn btn__primary">Remove completed</button>
    </div>
    
  </main>

<style>

    /* Reset */
    *,
    *::before,
    *::after {
      box-sizing: border-box;
    }
    /* end of reset */

    /* style for add todo section */
    .create{
        display: flex;
        flex-direction: column;
        align-items: center;
        
    }
    .create-input{
        width: 300px;
        height: 3em;
        font-size: 1em;
        margin-bottom: .5em;
    }
    .create-btn{
        padding: .5em;
        width: 30%;
        font-size: 1.2em;
        border-radius: .4em;
        border: none;
        color: white;
        background-color:black;
        margin-bottom: .5em;
    }
    /* end */


    /* Global styling for todo*/
    button {
      border: 1px solid black;
      margin: 0;
      padding: 0;
      width: auto;
      overflow: visible;
      background: transparent;
      color: inherit;
      font-family: inherit;
      font-size: 100%;
      line-height: 1.15;
      margin: 0;
      line-height: normal;
      -webkit-font-smoothing: inherit;
      -moz-osx-font-smoothing: inherit;
      -webkit-appearance: none;
    }

    button,
    input {
      overflow: visible;
    }
    input[type="text"] {
      border-radius: 0;
    }
    /* end of global styling for todo */



    /* Todos header */
    h2{
        text-align: center;
    }
    /* end */


    /* All todo container style */
    .todo-list{
        width: 90%;
        margin-bottom: 2em;
        text-align: center;
    }
    p{
        font-size: 1.3em;
        font-weight: bold;
    }
    /* end */

    /* style for each todo */
    
    .btn-group{
        display: flex;
        justify-content: center;
        gap: 1em;
        margin-top: 2em;
    }
    .btn-group > button {
        padding: 0.5em;
        border-radius: 1em;
  }
</style>