<script>
import { store } from '../store.js';

export default {
    name: 'AppFilter',
    data() {
        return {
            store
        }
    }
}
</script>

<template>
    <div class="container mb-5">
        <select v-model="store.filterType" @change="$emit('filterType')">
            <option value="">Seleziona un filtro</option>
            <option v-for="archetype in store.typeList" :value="archetype.archetype_name"> {{ archetype.archetype_name }} </option>
        </select>
    </div>
</template>

<style scoped lang="scss">

</style>