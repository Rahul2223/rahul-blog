<template>
  <div id="show-blogs">
    <h1>All Blog Articles</h1>
    <input type="text" v-model="search" placeholder="search blog">
    <div v-for="blog in filteredBlogs" :key="blog" class="single-blog">
      <router-link v-bind:to="'/blog/' + blog.id"><h2>{{blog.title | to-uppercase}}</h2></router-link>  
        <article>{{blog.body | snippet}}</article>
    </div>
  </div>
</template>

<script>
import searchMixin from "../mixins/searchMixins";

export default {
 
  data () {
    return {
      blogs: [],
      search: ""
    }
  }, 
  methods:{

  },
  created(){
      this.$http.get("https://jsonplaceholder.typicode.com/posts").then(function(data){
          this.blogs = data.body.slice(0,10);

      })
  },
  computed: {
    
  },
  filters:{
    toUppercase(value){
      return value.toUpperCase();
    }
  },
  directives:{
    'rainbow':{
      bind(el,binding,vnode){
        el.style.color = "#" + Math.random().toString(16).slice(2,8);
      }
    }
  },
  mixins: [searchMixin]
}
</script>

<style>
#show-blogs{
    max-width: 800px;
    margin: 0 auto;
}
.single-blog{
    padding: 20px;
    margin: 20px 0;
    box-sizing: border-box;
    background: "#eee";
}
</style>
