<template>
    <div class="container py-4">
      <select class="p-2 w-25 rounded-3" aria-label="Default select example" v-model="filterStatus" @change="$emit('search', filterStatus)">
        <option value="">All</option>
        <option :value="element.archetype_name" v-for="element in store.archetypesList">{{ element.archetype_name }}</option>
      </select>
    </div>
</template>

<script>
import axios from 'axios';
import { store } from '../data/store';

    export default {
        name:'SearchComponent',
        data() {
            return {
                filterStatus: '',
                store
            }
        },
        methods: {
            getArchetypes(){
                const url = store.apiArchetypes;
                axios.get(url).then((response) =>{
                    console.log(response.data);
                    store.archetypesList = response.data;
                })
            }
        },
        created(){
            this.getArchetypes()
        }
    }
</script>

<style lang="scss">

</style>