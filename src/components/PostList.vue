<template>
    <div class="container">
        <h1>Listado de Posts <button class="btn btn-primary">Estilado con Bootstrap</button></h1>
        <ul class="postList">
            <li v-for="post in posts" :key="post.id">{{ post.id + ". " + post.title }}</li>
        </ul>
    </div>
</template>

<script lang="ts" setup>
    import PostService from '@/services/PostService';
    import { onMounted } from 'vue';

    const service = new PostService()
    const posts = service.getPosts()

    onMounted( async() => {
        await service.fetchAll()
    })


    /* import { defineComponent, onMounted } from 'vue';
    import PostService from '@/services/PostService';
    export default defineComponent({
        name: 'PostList',
        setup(){
            const service = new PostService()
            const posts = service.getPosts()

            onMounted( async () => {
                await service.fetchAll()
            })

            return {posts}
        }
    }) */
</script>

<style scoped lang="scss">

    .container{
        display: flex;
        flex-direction: column;
        align-items: center;
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;

        .postList{
            width: 95vw;
            height: 75px;
            padding: 20px;
            list-style-type: none;

            li{
                width: 100%;
                padding: 10px;
                color: $black;
                font-size: 18px;
                text-align: center;
                border: 1px solid #ccc;
            }
        }
    }
</style>