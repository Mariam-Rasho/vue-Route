<script>
import TodoItem from "./TodoItem.vue"
    export default {
        components: {
            TodoItem
        },

        // NOTE:
        //!to import data from perant
        props: {
            title: String,
            todoArray: Array,
        },
        data() {
            return {
                textSearch: ""
            }
        },
        computed: {
            filterByType() {
                if (this.textSearch == "")
                    return this.todoArray
                // console.log(this.textSearch);
                else {
                    return this.todoArray.filter(task => task.type === this.textSearch)
                }
            },
        }
    }
</script>
<template>

    <div class="container my-5 p-3 rounded row col-md-4"  v-show="todoArray.length">
<div class="d-flex justify-content-between  align-items-center ">
    <h1 class="h2 text-center text-white">{{title}}: {{todoArray.length}}</h1>
    <span class="input-box col-md-3">
        <input type="search" class="form-control" placeholder="Search.." v-model="textSearch" @search="filterByType">
    </span>
</div>
    <ul class="h4 list-unstyled text-justify text-dark mt-2">
        <TodoItem v-for="todo in filterByType" :key="todo.id" :todo="todo"></TodoItem>
    </ul>
    </div>

</template>