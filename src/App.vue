<template>
  <div>
    <app-header></app-header>
    <router-view></router-view>
  </div>
</template>

<script>
import addBlog from "./components/addBlog.vue"
import showBlog from "./components/showBlog.vue"
import listBlogs from "./components/listBlogs.vue"
import header from "./components/header.vue"

export default {
  components:{
    "add-blog": addBlog,
    "show-blog": showBlog,
    "list-blog" :listBlogs,
    "app-header": header
  },
  data () {
    return {
      
    }
  }, 
  methods:{

  }
}
</script>

<style>
body{
  margin: 0;
  font-family: "Nunito Semibold";
}
</style>
