<template>
  <header>    
    <div class="container text-center">
    <a class='back-btn'  ><img src="https://img.icons8.com/flat_round/64/000000/back--v1.png"/></a>
    
    <h1 class=''>MY TASKS</h1>
    </div>
  </header>
 
  <div class="wrapper">
    <div class="container text-center">
      <form @submit.prevent="addTodo">
        <input type="text" class="form-control" name="todo-text" v-model="newTodoText" placeholder="New todo">
      </form>
    </div>
    <div class='container task-list-container'>
      <ul v-if="todos.length">
        <TodoItem v-for="todo in todos" :key="todo.id" :todo="todo" @remove="removeTodo"/>
      </ul>
      <p class="none" v-else>Nothing left in the list. Add a new todo in the input above.</p>
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue"

let nextTodoId = 1

const createTodo = text => ({
  text,
  id: nextTodoId++
})

export default {
  components: {
    TodoItem
  },

  data() {
    return {
      todos: [
        createTodo("Learn Vue"),
        createTodo("Learn about single-file components"),
        createTodo("Learn about SPA")
      ],

      newTodoText: ""
    }
  },

  methods: {
    addTodo() {
      const trimmedText = this.newTodoText.trim()

      if (trimmedText) {
        this.todos.push(createTodo(trimmedText))
      }

      this.newTodoText = ""
    },

    removeTodo(item) {
      this.todos = this.todos.filter(todo => todo !== item)
    }
  }
}
</script>

<style >
*, *::before, *::after{ 
  box-sizing: border-box
}
html, body{
  font: 16px/1.2 BlinkMacSystemFont, -apple-system, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  padding: 10px
}
.wrapper{
  width: 75%;
  margin: 0 auto
}
form{
  margin-bottom: 20px
}
input[type="text"]
{  width: 100%;
  padding: 10px;
  border: 1px solid #777
}
ul, li{
  margin: 0;
  padding: 0
}
p.none{
  color: #888;
  font-size: small
}
.create-task-btn{
	border : 1px solid #4CAF50;
	padding: 10px;
	border-radius: 20px;
	transition-duration: 0.4s;
	background-color: #27ae60; /* Green */
  color: white;
  float: left;
  margin-left: 10px;
}

.create-task-btn:hover {
  background-color: #4CAF50 ;
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2), 0 6px 20px 0 rgba(0,0,0,0.19);
}

form{
	margin-top: 30px;
}

#task-input{
	border-radius: 20px;
	float: left;
	width: 70%;
	padding: 20px;
	margin-left: 50px;
}

.task-list-container{
	margin-top: 30px;
}

ul{
	list-style-type: none;
}

ul li{
	background-color: white;
	margin: 10px;
	padding: 5px 10px;
	font-size: 1.2em;
	border-radius: 10px;
	opacity: .9;
}

li:hover{
	text-decoration: line-through;
	background-color: #bdc3c7 ;
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2), 0 6px 20px 0 rgba(0,0,0,0.19);
  cursor: pointer;
}

.done{
  text-decoration: line-through;
  background-color: #bdc3c7 ;
}
</style>
