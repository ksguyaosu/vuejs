<template>
    <div>
        <post-form @create="createPost" @delete="deletePost"/>  
        <post-list />
        <div class="post" v-for="post in posts" v-bind:key="post.body">            
            <div><strong>Название:</strong> {{ post.title }} </div>       
            <div><strong>Описание:</strong> {{ post.body }}</div>
            <!-- <button class="delBTN" v-on:click="deletePost">Удалить</button>               -->
        </div>  
        <post-item :posts="posts"/>
        <empty-list v-if="posts.length ==  0"/>
        
        
    
    </div>    
    
</template>

<script>

import PostForm from "./components/PostForm.vue";
import PostList from "./components/PostList.vue";
import PostItem from "./components/PostItem.vue";
import EmptyList from "./components/EmptyList.vue";
export default {
    components: {
     PostForm, PostList, PostItem, EmptyList
},
    data() {
        return {
            
            posts: [
                 
            ],
                       

        }
    }, 
    methods: {
       createPost(post) {
           this.posts.push(post)
       },
       deletePost(post) {
           this.posts.splice(post)
       }
        
    }
}
</script>

<style>
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        
    }

   .post {
        padding: 15px;
        border: 2px solid blue;
        margin: 15px;
    }

    .formClass {
        text-align: center;
    }

    .inputClass {
        padding: 7px;
        margin: 7px;
        border: 1px solid blue;
    }

    .buttonClass{         
        padding: 7px;
        border: 1px solid blue;
        background: none;
        margin: 7px;
    }
    
    .delBTN {
        padding: 7px;
        border: 1px solid blue;
        background: none;
        margin-top: 10px;
    }
 
</style>