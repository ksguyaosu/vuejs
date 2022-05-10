<template>
    <div class="post" v-for="post in posts" v-bind:key="post.body">            
        <div><strong>Название:</strong> {{ post.title }} </div>       
        <div><strong>Описание:</strong> {{ post.body }}</div>              
    </div>
</template>
<script>
export default {
    props: {
        post: {
            type: Array,
            required: true
        }
    }
}
</script>
<style></style>