<template>
  <div>
    <section class="hero is-small is-primary">
      <div class="container">
        <div class="hero-head has-text-centered">
        <h2 class="title">News Sources</h2>
      </div>

      <div class="hero-body">
        <label class="label">News Sources</label>

        <div class="field has-addons">

  <p class="control">
    <span class="select">
      <select v-on:change = "ChangeSource">
        <option v-bind:value="source.id" v-for="source in sources">{{source.name}}</option>
      </select>
    </span>
  </p>
  <p class="control"><a type="button" v-bind:href="source.url" class="button is-warning " target="_blank">Goto Site</a></p>
    </div>
    <p class="subtitle is-small" >{{source.description}}</p>

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
      sources: [],
      source : ' ',
      ts: ' '

    }
  },
  created(){
    this.$http.get('https://newsapi.org/v1/sources?language=en').then(function(data){
      return data.json();
    }).then(function(data){
    //  console.log(data);
    this.sources = data.sources;

    //  console.log(tarr);
    });
  },
  methods: {
    ChangeSource: function(e){
      for(var i=0;i<this.sources.length;i++){
        if(this.sources[i].id == e.target.value){
          this.source = this.sources[i];
          this.id = this.sources[i].id;
          //console.log(this.id);
          bus.$emit('Headlines',this.id);
        }
      }
    }
  }
}
</script>

<style>
.hero-head{
  margin-top: 30px;
}
</style>
