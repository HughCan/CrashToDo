<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add ToDo item...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

//Add logic to ensure that the input box has a minimum amount of data in it, otherwise don't attempt to add the new item to the list

<script>
export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {   
        addTodo(e) {
            e.preventDefault();
            const newTodo = {
                title: this.title,
                completed: false
            }
            //send up to parent
            this.$emit('add-todo', newTodo)
            this.title = '';
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }
    input[type="text"] {
        flex: 10;
        padding: 10px;
    }
    input[type="submit"] {
        flex: 2
    }
</style>