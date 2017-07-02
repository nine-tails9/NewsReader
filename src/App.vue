<template>
  <div id="app">
    <news-List></news-List>

  </div>
</template>

<script>
import ListN from './components/NewsList.vue';
export default {
  components: {
    'news-List': ListN
  },
  name: 'app',
  data () {
    return {

    }
  }
}
</script>

<style>

</style>
