<template>
    <li>
        <span :class="{done:todo.completed}">
            <input type="checkbox" @change="todo.completed = !todo.completed">
            <strong>{{ idx + 1 }}</strong>
            <span class="title"> {{ todo.title }} </span>
        </span>
        <button @click="$emit('remove-todo', todo.id)">&times;</button>
    </li>
</template>

<script>
    export default {
        props:  {
            todo: {
                type: Object, 
                required: true
            },
            idx: Number,
        },
    }
</script>

<style scoped>

li {
    max-width: 800px;
    margin: 1rem auto;
    display: flex;
    justify-content: space-between;
    font-size: 1.5rem;
}

button {
    width: 40px;
    height: 40px;
    border-radius: 50px;
    color: #fff;
    background-color: red;
    font-size: 1.5rem;
    border: none;
    outline: none;
    cursor: pointer;
    transition: all .2s linear;
}

strong {
    font-weight: bold;
    color: #fff;
    margin-right: 5px;
    margin-left: 15px;
}

button:hover {
    background-color: darkred;
}

button:active {
    background-color: #fff;
    color: red;
}


input {
    cursor: pointer;
}

.done {
    text-decoration: line-through;
}

</style>