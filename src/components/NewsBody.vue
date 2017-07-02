<template>
  <div>
    <section class="hero is-dark" v-for="items in content">
      <h3 hero-head class="title has-text-centered is-3">{{items.title}}</h3>
      <div class="hero-body">

      <div class="container" >

          <p class="subtitle">
            {{items.description}}
          </p>
          <a v-bind:href="items.url">Read More</a>


      </div>

    </div>

    </section>
  </div>
</template>

<script>
import { bus } from '../main';

export default {
  props: {
    id: {
      type: String,
      required: true
    }
  },
  data () {
    return {
      content: []

    }
  },
  created(){
    bus.$on('Headlines',(data) =>{
      this.id = data;
    });
    this.$http.get('https://newsapi.org/v1/articles?source=' + this.id + '&apiKey=712bc1362cc14cb8aaee1db8d8b43c5b').then(
      function(data){
        return data.json();
      }).then(function(data){
          this.content = data.articles;
          console.log(this.content);

      });

  }
}
//712bc1362cc14cb8aaee1db8d8b43c5b
</script>


<style>
</style>
