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
  <div>
    <h2>Todo Application</h2>
    <hr>
    <router-view />
  </div>
</template>

<style scoped>
</style>
