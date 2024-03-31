<script>
    import TodoList from "./TodoList.vue"
    import TodoAdd from "./TodoAddItem.vue"
    import TodoLoad from "./TodoLoad.vue"
    export default {
        components: {
            TodoList,
            TodoAdd,
            TodoLoad
        },

        data() {
            return {
                todos: [
                    { id: 1, title: "study vue js from docs", isCompleted: true, type: "course" },
                    { id: 2, title: "read the js tutorial", isCompleted: false, type: "course" },
                    { id: 3, title: "do the homework", isCompleted: true, type: "design" },
                    { id: 2, title: "solve the vue tutorial", isCompleted: false, type: "homework" },
                ],

            }
        },
        computed: {
            filteredArray() {
                return {
                    done: this.todos.filter((a) => a.isCompleted),
                    inProgress: this.todos.filter((a) => !a.isCompleted),
                }

            }
        },
        methods: {
            addNewTodo(newTodo, newType) {
                // if (newTodo == "" || newType == "")
                //     return
                this.todos.push({ id: this.todos.length++, title: newTodo, isCompleted: false, type: newType })
            },

        },

    }
</script>
<template>

    <div id="bg-todos">
        <TodoAdd @add="addNewTodo"></TodoAdd>
        <TodoList class="inProgress" title="In Progress" :todoArray="filteredArray.inProgress"></TodoList>
        <TodoList class="done" title="Done" :todoArray="filteredArray.done"></TodoList>
        <TodoLoad></TodoLoad>
    </div>

</template>

<style scoped>
#bg-todos{
    padding-top: 80px;
        width: 100vw;
        height: 100vh;
        background-image: url(../assets/pexels-content-pixie-2736499.jpg);
        background-repeat: no-repeat;
        background-position: center;
        background-size: cover;
        /* height: 100vh; */
        overflow: auto;

}
</style>