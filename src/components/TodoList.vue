<script>
    import TodoItem from './TodoItem.vue';

    export default {
        props:  ['todos'],
        components: {
            TodoItem
        },
        methods: {
            removeTodo(id) {
                this.$emit('remove-todo', id)
            }
        },
    }
</script>

<template>
    <div>
        <ul>
            <TodoItem 
                v-for="(todo, i) of todos"
                :todo="todo"
                :idx="i"
                @remove-todo="removeTodo"
            />    
        </ul>
    </div>
</template>


<style scoped>

ul {
    margin: 0;
    padding: 0;
}

</style>