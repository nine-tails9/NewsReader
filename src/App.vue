<template>
  <div id="app">
    <news-List v-bind:id='id'></news-List>
    <news-Body v-bind:id='id'></news-Body>

  </div>
</template>

<script>
import ListN from './components/NewsList.vue';
import BodyN from './components/NewsBody.vue';
export default {
  components: {
    'news-List': ListN,
    'news-Body': BodyN
  },
  name: 'app',
  data () {
    return {
      id: 'cnn'
    }
  }
}
</script>

<style>

</style>
