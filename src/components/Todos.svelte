<script>
</script>

<div>
  <form class="create">
    <h2 class="create-label">
        What needs to be done?
    </h2>
    <input type="text" id="todo-0" class="create-input"/><br/>
    <button type="submit"  class="create-btn">
      Add
    </button>
  </form>
  
   <div class="filter-btns">
    <button class="filter-btn toggle-btn" >
      All
    </button>
    <button class="filter-btn toggle-btn" aria-pressed="false">
     Active
    </button>
    <button class="filter-btn toggle-btn" aria-pressed="false">
     Completed
    </button>
  </div>

    <h2>2 out of 3 items completed</h2>
    <div class="todo-list">
       <div class="todo">
        <div class="todo-header">
            <input type="checkbox" class="todo-check" id="todo-name">
            <label for="todo-name" class="todo-name">Create Svelte App</label>
        </div>
        <div class="todo-btn-group">
            <button>Edit</button>
            <button class="danger">Delete</button>
        </div>
       </div>
       <div class="todo">
        <div class="todo-header">
            <input type="checkbox" class="todo-check" id="todo-name">
            <label for="todo-name" class="todo-name">Create Svelte Components</label>
        </div>
        <div class="todo-btn-group">
            <button>Edit</button>
            <button class="danger">Delete</button>
        </div>
       </div>
    </div>

    <hr />
    <!-- MoreActions -->
  <div class="btn-group">
    <button type="button" class="btn btn__primary">Check all</button>
    <button type="button" class="btn btn__primary">Remove completed</button>
  </div>
  
</div>

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
}
/* end */

/* style for each todo */
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