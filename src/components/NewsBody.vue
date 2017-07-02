<template>
  <div class="hero is-light is-bold" >
    <section class="wid" v-for="items in content">
      <hr class="hori">

      <h3 hero-head class="title has-text-centered is-3">{{items.title}}</h3>
      <figure class="image">
        <img v-bind:src="items.urlToImage">
      </figure>
      <div class="hero-body">

        <br>
      <div class="content is-light">
          <p class="is-light cool" >
            {{items.description}}

          </p>
      </div>
      <a v-bind:href="items.url" class="button is-dark is-pulled-right">Read More</a>
<span class="tag is-dark is-pulled-left">{{items.author}}</span>
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
.wid{
  width: 80%;
  margin-left: 100px;
  margin-top: 80px;
}
.image{
  width: 500px;
  margin-left: 25%;
  margin-top: 60px;
}
.hori{
  width: 90%;
  margin-left: 10%;
  color: rgb(10, 3, 17);
  height: 2px;

}
</style>
