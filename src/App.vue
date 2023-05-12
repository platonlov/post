<script>
export default {
  data() {
    return {
      titl: "",
      name: "",
      posts:[
      {id: 1, title:"First post :0", body:"Write your first post!"}
    ]
    }

  }, 
  methods: {
    create() {
      const newpost = {
        id: Date.now,
        title: this.titl,
        body: this.name
        
      }
      this.posts.push(newpost)
      this.titl = ''
      this.name = ''
    },
    dele(el) {
      this.posts.splice(el,1)
    }
  }

}
</script>

<template>
  <form action="" @submit.prevent>
    <h1 style="text-align: center;color: white;">Add your post</h1>
    <input v-model="titl" class="input" type="text" placeholder="Title"> <br>
    <input v-model="name" type="text"  class="input" placeholder="Description"> <br>
    <button class="create" @click="create()">Create</button>
  </form>
  <div class="posts" v-for="(post, index) in posts">
    <div> <b>Title: </b> {{ post.title }}</div>
    <div><b>Description: </b> {{ post.body }} <img src="https://cdn-icons-png.flaticon.com/512/73/73806.png" alt="Delete" class="img" v-on:click="dele(index)"></div>
    
  </div>
</template>

<style> 
body {
  background-color: gray;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Inter";
}
.input {
  width: 100%;
  height: 50px;
  border: 2px solid #353333;
  border-radius: 5px;
  margin: 5px;
  text-align: center;
}
.create {
  border: 2px solid #353333;
  border-radius: 3px;
  width: 100%;
  margin: 5px;
  padding: 5px;
  background-color: #CCCCCC;
}
.posts {
  background-color: rgb(150, 149, 149);
  margin: 15px;
  padding: 15px;
  border: 2px solid whitesmoke;
}
.posts .img {
  width: 5%;
  height: 5%;
  cursor: pointer;
}

@font-face {
  font-family: "Inter";
  src: url('./fonts/Inter/Inter.ttf');
  font-size: normal;
  font-weight: normal;
}
</style>