<template>
    <form action="" @submit.prevent='onSubmit'>
        <input type="text" name="" id="" v-model="title">
        <button type="submit">Create</button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            title:''
        }
    },

    methods: {
        onSubmit() {
            if (this.title.trim()) {
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

<style  scoped>
    form {
        display: flex;
        justify-content: center;
    }

    input {
        width: 400px;
        outline: none;
        border: 1px solid indigo;
        
    }

    button {
        margin-left: 10px;
        background-color: indigo;
        color: #fff;
        outline: none;
        border: none;
        border-radius: 10%;
        cursor: pointer;
    }

    button:hover {
        transform: translateY(-3px);
        box-shadow: 0 3px 5px rgb(0, 0, 0);
        transition: all .2s;
    }

    button:active {
        box-shadow: 0 1px 2px rgb(0, 0, 0);
        transform: translateY(0);
        transition: all .2s;
    }
</style>