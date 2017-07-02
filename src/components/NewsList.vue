<template>
  <div>
    <section class="hero is-small is-primary">
      <div class="container">
        <div class="hero-head has-text-centered">

        <h2 class="title">News Sources </h2>

      </div>
      <div class="hero-body">
        <div class="field">
  <label class="label">News Sources</label>
  <p class="control">
    <span class="select">
      <select>
        <option v-for="source in sources"></option>
      </select>
    </span>
  </p>
</div>

      </div>

      </div>

    </section>

  </div>
</template>

<script>
export default {
  data () {
    return {
      sources: []

    }
  },
  created(){
    this.$http.get('https://newsapi.org/v1/sources?language=en').then(function(data){
      return data.json();
    }).then(function(data){
    //  console.log(data);
      var tarr = [];
      for(let name in data){
        if(name=="sources"){
          for(let id in name){
            console.log(id);
          }
        }
        //tarr.push(data[name].name);

      }
    //  console.log(tarr);
    });
  }
}
</script>

<style>
.hero-head{
  margin-top: 30px;
}
</style>
