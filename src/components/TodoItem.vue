<script>
    export default {
        props: {
    todo: {
      type: Object,
    }
},
    }
</script>
<template>
    <li class="my-4 rounded py-2 px-3 iTodo">
            <label class="d-flex justify-content-between">
                {{todo.title}}
                <input type="checkbox"
                :v-model="todo.isCompleted" />
            </label>
            </li>
</template>