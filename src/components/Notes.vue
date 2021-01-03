<template>
    
    <header>
    <div class="container text-center">
        <a class='back-btn'><img src="https://img.icons8.com/flat_round/64/000000/back--v1.png"/></a>
        <h1 class=''>MY NOTES</h1>
    </div>
    </header>
    <div class="container form-container">
    <form id = 'notes-form' @submit.prevent="addTodo" >
        <div class="form-group">
            <input type="text" class="form-control " id="" placeholder="title" v-model="newTodoTitle">
        </div>
        <div class="form-group">
            <textarea class="form-control" id="" rows="5" placeholder="note" v-model="newTodoText"></textarea>
        </div>
        <button type="submit" class="btn btn-primary" >Create</button>
    </form>
    </div>
    <div  class="container note-list">
        <div id='notes-list' class="row" v-if="todos.length">
            <NotesItem v-for="todo in todos" :key="todo.id" :todo="todo" @remove="removeTodo"/>
        </div>
        <p class="none" v-else>Nothing to show</p>
    </div>
</template>

<script>
import NotesItem from './NotesItem.vue'


let nextTodoId = 1

const createNote = (title, text) => ({
  title,
  text,
  id: nextTodoId++
})

export default {
  components: {
    NotesItem
  },

  data() {
    return {
      todos: [
        createNote("Learn Vue", "uuoiu"),
        createNote("Learn about single-file components", "jjkk"),
        createNote("Learn about SPA", "hjkh")
      ],
      newTodoTitle:"",
      newTodoText: ""
    }
  },

  methods: {
    addTodo() {
      const trimmedTitle = this.newTodoTitle.trim()
      const trimmedText = this.newTodoText.trim()
      
      if (trimmedTitle) {
        this.todos.push(createNote(trimmedTitle))
        this.todos.push(createNote(trimmedText))
      }

      if (trimmedText) {
        this.todos.push(createNote(trimmedText))
      }

      this.newTodoTitle = ""
      this.newTodoText = ""
      
    },

    removeTodo(item) {
      this.todos = this.todos.filter(todo => todo !== item)
    }
  }
}
</script>