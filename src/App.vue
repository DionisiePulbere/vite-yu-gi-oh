<script>
import axios from 'axios';
import { store } from './store.js';
import AppHeader from './components/AppHeader.vue';
import AppCardsList from './components/AppCardsList.vue';
import AppFilter from './components/AppFilter.vue';


export default{
  components: {
    AppHeader,
    AppCardsList,
    AppFilter,
   
  },
  data () {
    return{
      store,
      queryParams: {
        num: 20,
        offset: 0
      }
    }
  },
  methods: {
    getCardsFromApi() {
      axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php", { params: this.queryParams })
      .then((response) => {
        store.cards = response.data.data;
      });
    },

    getTypeFromApi(){
      axios.get("https://db.ygoprodeck.com/api/v7/archetypes.php")
      .then((response) => {
        store.typeList = response.data;
      })
    },
    filterTypeApi(){
      if (store.filterType !== ""){
        this.queryParams.archetype = store.filterType;
      } else {
        this.queryParams.archetype = "";
      };
      axios.get("https://db.ygoprodeck.com/api/v7/cardinfo.php", { params: this.queryParams })
				.then((response) => {
				store.cards = response.data.data;
				})
    }
  },

  mounted() {
    this.getCardsFromApi(),
    this.getTypeFromApi()
  }
}
</script>

<template>
  <AppHeader></AppHeader>
  <main class="p-5">
    <AppFilter @filterType="filterTypeApi"></AppFilter>
    <AppCardsList></AppCardsList>
  </main>
</template>

<style lang="scss">
@use './style/generic'
</style>
