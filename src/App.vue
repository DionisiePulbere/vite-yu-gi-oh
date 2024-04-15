<script>
import axios from 'axios';
import { store } from './store.js';
import AppHeader from './components/AppHeader.vue';
import AppCardsList from './components/AppCardsList.vue';

export default{
  components: {
    AppHeader,
    AppCardsList,
  },
  data () {
    return{
      store
    }
  },
  methods: {
    getCardsFromApi() {
      axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
      .then((response) => {
        console.log(response.data.data);
        store.cards = response.data.data;
      });
    }
  },
  mounted() {
    this.getCardsFromApi()
  },
}
</script>

<template>
  <AppHeader></AppHeader>
  <main class="p-5">
    <AppCardsList></AppCardsList>
  </main>
</template>

<style lang="scss">
@use './style/generic'
</style>
