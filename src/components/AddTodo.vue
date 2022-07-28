<template>
    <form @submit.prevent="onSubmit">
        <input type="text" placeholder="Add new todo:" v-model="title">
        <button type="submit">Add</button>
    </form>
</template>

<script>
    export default {
        data() {
            return {
                title: ''
            }
        },
        methods: {
            onSubmit() {
                if(this.title.trim()) {
                    const newTodo = {
                        id: Date.now(),
                        title: this.title,
                        completed: false
                    }
                    this.$emit('add-todo', newTodo)
                    this.title = ''
                }
            }
        }
    }
</script>

<style scoped>
    form {
        width: 800px;
        margin: 2rem auto;
    }

    input {
        width: 80%;
        border-radius: 10px;
        padding: 1rem;
        border: none;
        outline: none;
        color: #fff;
        background-color: #333232;
        font-size: 1.5rem;
    }
    button {
        width: 15%;
        border: none;
        outline: none;
        border-radius: 10px;
        padding: 1rem;
        font-size: 1.5rem;
        margin-left: 5%;
    }
</style>