<script >
  import TodoList from '@/components/TodoList.vue'
  import AddTodo from './components/AddTodo.vue'


  export default {
    components: {
      TodoList,
      AddTodo
    }, 
    data () {
      return {
        todos: [
          {id: 1, title: 'wake up', comleted: false},
          {id: 2, title: 'brash your teeth', comleted: false},
          {id: 3, title: 'take a shower', comleted: false},
        ]
      }
    },
    mounted() {
      fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
      .then(response => response.json())
      .then(json => {
        this.todos = json
      })
    },
    methods: {
      removeTodo(id) {
        this.todos.forEach((item, idx) => {
          if(item.id == id) this.todos.splice(idx, 1);
        });
      },
      addTodo(todo) {
        this.todos.push(todo)
      }
    }
  }


</script>

<template>
  <div id="app">
    <h1>Todo Application</h1>
    <AddTodo
      @add-todo="addTodo"
    />
    <hr>
    <center v-show="this.todos.length == 0">
      <br><br>
      <h2>No todos creaded!</h2>
    </center>
    <TodoList 
      :todos="todos"
      @remove-todo="removeTodo"
    />
  </div>
</template>

<style scoped>
</style>
