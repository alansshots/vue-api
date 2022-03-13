<template>
  <div id="comments">
      <div class="form">
          <p>Post Title:</p>
          <input type="text" v-model="title">
          <br>
          <p>Post Content:</p>
          <textarea cols="30" rows="10" v-model="content"></textarea>
          <br>
          <button @click="sendPostHandler">POST!</button>
      </div>
            <br>
      <div id="posts">
          <button @click="getPostsHandler">Fetch Comments</button>
          <!-- include Post component here -->
          <Post v-for="(post,index) in posts"
          :key="index"
          :title="post.title"
          :body="post.body"
          />
      </div>
  </div>
</template>

<script>
import PostsFetch from '../mixins/Posts-fetch.vue'
import Post from './Post.vue'

export default {
    name:'Comments',
    components: {
        Post
    },
    mixins: [PostsFetch],
    data(){
        return {
            posts: null,
            title: null,
            content: null
        }
    },
    methods: {
        getPostsHandler(){
            this.getPosts()
            .then((res) => {
                this.posts = res
                console.log(res)
            })
        },

        sendPostHandler(){
            this.sendPost(this.title, this.content)
            .then((res) => {
                this.posts = res
                console.log(res)
            })
        }
    }

}
</script>

<style scoped>
 .form {
     width: 500px;
     margin: auto;
     display: flex;
     flex-direction: column;
 }
</style>