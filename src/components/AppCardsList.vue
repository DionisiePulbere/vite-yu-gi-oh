<script>
import { store } from '../store.js';
import AppCard from './AppCard.vue';
import AppTotal from './AppTotal.vue'

export default {
    name: 'AppCardsList',
    components: {
        AppCard,
    },
    data(){
        return{
            store
        }
    }
}
</script>

<template>
    <section>
        <div class="container p-4 d-flex flex-wrap">
           
            <AppCard v-for="card in store.cards" :key="card.id" :cardInfo="card"></AppCard>
            
        </div>
    </section>
</template>

<style scoped lang="scss">
.container{
    background-color: white;
    
}

</style>