<template>
    <div>
        <post-form @create="createPost" @delete="deletePost"/>  
        <post-list />
        <div class="post" v-for="post in posts" v-bind:key="post.body">   
            <div class="emoji"><strong>⭐</strong></div> 
            <div class="postInput"><strong>ID: </strong> {{ post.id }}</div>        
            <div class="postInput"><strong>Название:</strong> {{ post.title }} </div>       
            <div class="postInput"><strong>Описание:</strong> {{ post.body }}</div>
            <div class="postInput"><strong>Автор:</strong> {{ post.author }}</div>
            <vkontakte-button url="document.location.href" description=":-)" />
  
            <!-- <button class="delBTN" v-on:click="deletePost">Удалить</button>               -->
        </div>  
        <iframe class="videoScreen" width="300" height="180" src="https://www.youtube.com/embed/5qap5aO4i9A?autoplay=1" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen ></iframe>
        <post-item :posts="posts"/>
        <empty-list v-if="posts.length ==  0"/>
        
        
    
    </div>    
    
</template>

<script>

import PostForm from "./components/PostForm.vue";
import PostList from "./components/PostList.vue";
import PostItem from "./components/PostItem.vue";
import EmptyList from "./components/EmptyList.vue";
import VkontakteButton from "vue-share-buttons/src/components/VkontakteButton";

export default {
    components: {
     PostForm, PostList, PostItem, EmptyList, VkontakteButton
},
    data() {
        return {
            
            posts: [
                {id: Date.now(), title: 'Joeee', body: 'Biden', author: 'Misha'},
                {id: Date.now(), title: 'Корней', body: 'Корнеевич', author: 'Корнеплод'},
                {id: Date.now(), title: 'Че', body: 'В данном эссе я рассмотрю две большие темы: Антропоморфизм и объективные методы изучения поведения животных. История теорий и господствующих взглядов по каждой из этих тем будут рассмотрены в хронологическом порядке.Понятие антропоморфизма (от аnthrаpоs - человек, mоrphe - форма) относится к периоду донаучных знаний о поведении животных и заключается в приписывании животным человеческих качеств (зависть, злоба, радость и т.д.). В то время это был единственный способ объяснения поведения  животных, а человеку достаточно было тех знаний, которыебыли нужны ему для выживания среди животных, для охоты за ними и для выделки одежды из шкур. Одна из актуальных задач современной науки о поведении - преодолениеантропоморфизма.', author: 'Misha'}
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

    .emoji {
        text-align: center;
        margin-bottom: 15px;
        font-size: 20px;
    }

    .postInput {
        text-align: center;
    }

    .videoScreen {
        position: absolute;
        right: 50px;
        bottom: 50px;
    }
 
</style>