<script>
    export default {

        data() {
            return {
                postes: [],
                done: false
            };
        },
        created() {
                fetch("https://jsonplaceholder.typicode.com/posts")
                    .then((response) => response.json())
                    .then((data) => {
                        this.postes = data;
                    },
                    );
            },
        }

</script>

<template>
    <div class="list-unstyled my-3 container ms-5 p-3 rounded" style="width:450px" >
    <button
    @click="postes ,done=!done" v-text="done ? 'hide todos' :'loading..' "
    class="form text-light btn-lg btn form px-4 fw-bold rounded-pill ms-5"
>
</button>
<ul class="list-unstyled">
    <li v-show="done"   v-for="post in postes.filter(a=> (a.id <= 10))"   :key="post.id" class="mt-2 p-3 rounded h6 ms-5 listLoad"><span>{{post.id}}</span> : {{post.title}} </li>
</ul>
    </div>
</template>