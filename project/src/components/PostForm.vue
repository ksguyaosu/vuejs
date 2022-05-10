<template>
    <div>
        <form class="formClass" @submit.prevent>
           <h2>Создание поста</h2>
           <input v-model="post.title" class="inputClass" type="text" placeholder="Название">
           <input v-model="post.body" class="inputClass" type="text" placeholder="Описание">
           <button class="buttonClass" v-on:click="createPost">Отправить</button>
           <button class="buttonClass" v-on:click="deletePost">Удалить все</button>
        </form>
    </div>
</template>

<script>
export default {

    data() {
        return {
            post: {
                title: '',
                body: ''
            }
        }
    },
    methods: {
        createPost() {             
            this.post.id = Date.now();
            this.$emit('create', this.post)
            this.post = {
                title: '',
                body: ''
            }          
        },
        deletePost() {
            this.post.id = Date.now();
            this.$emit('delete', this.post)
            this.post = {
                title: '',
                body: ''
            }
        }
    }
}
</script>

<style scoped>

</style>