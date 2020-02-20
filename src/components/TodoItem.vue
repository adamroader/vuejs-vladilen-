<template>
    <li>
        <span v-bind:class='{done: todo.completed}'>
            <input type="checkbox" 
            v-on:change="todo.completed = !todo.completed">
            <strong>{{index+1}}</strong>
            {{todo.title}}
        </span>
        <button class="rm" v-on:click="$emit('remove-todo', todo.id)">&times;</button>
    </li>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            required: true 
        },

        index: Number
    }
}
</script>

<style scoped>
    li {
        border: 1px solid #ccc;
        display: flex;
        justify-content: space-between;
        padding: .5rem 2rem;
        margin-bottom: 1rem;

    }

    .rm {
        background: red;
        color: #fff;
        border-radius: 10%;
        border: none;
        outline: none;
        font-weight: bold;
        cursor: pointer;
    }

     .rm:hover {
        transform: translateY(-3px);
        box-shadow: 0 3px 5px rgb(0, 0, 0);
        transition: all .2s;
    }

    .rm:active {
        box-shadow: 0 1px 2px rgb(0, 0, 0);
        transform: translateY(0);
        transition: all .2s;
    }

    input {
        margin-right: 1rem;
    }

    .done {
        text-decoration: line-through;
    }
</style>

