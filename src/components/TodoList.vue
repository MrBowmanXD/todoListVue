<template>
    <h1>
        {{ title }}
    </h1>
    <label for="todo">Todo</label>
    <input type="text" name="todo" v-model="Todo">
    <label for="priority">Priority</label>
    <input type="text" name="priority" v-model="priority">
    <button @click="SaveTodo">
        Enter
    </button>
    <ul>
        <li v-for="todo in todoList" :key="todo.todo">
            {{ todo.todo }} - priority: {{ todo.priority }}
            <button @click="showForm(todo)">Show update form</button>
            <div class="updateInput" v-if="todo.update">
                <label for="updateTodo">Update Todo</label>
                <input type="text" name="updateTodo" v-model="updateTodo">
                <label for="updatePriority">Update Priority</label>
                <input type="text" name="updatePriority" v-model="updatePriority">
                <button @click="updateTodoWithForm(todo)">Update</button>
            </div>
            <button @click="deleteTodo(todo)">Delete todo</button>
        </li>
    </ul>
</template>

<script>
export default {
    name: "TodoList",
    data() {
        return {
            title: "Todo List",
            priority: "",
            Todo: "",
            id: 0,
            updateTodo: "",
            updatePriority: "",
            todoList: []
        }
    },
    methods: {
        SaveTodo() {
            let todo = this.Todo;
            let priority = this.priority;
            this.id += 1;
            let currentId = this.id;
            this.todoList.push({todo, priority, id: currentId, update: false});
        },
        showForm (todo) {
            todo.update = !todo.update;
        },
        updateTodoWithForm(todo) {
            this.todoList.forEach((el) => {
                if (el.id === todo.id) {
                    todo.todo = this.updateTodo;
                    todo.priority = this.updatePriority;
                    this.showForm(todo);
                }
            });
        },
        deleteTodo (todo) {
            this.todoList.forEach((el, index) => {
                if (el.id === todo.id) {
                    this.todoList.splice(index, 1);
                }
            });
        }
    }
}
</script>

<style scoped>
</style>
