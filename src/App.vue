<template>
  <div>
    <!-- <HeaderComponent title="Yu-Gi-Oh Api"/> -->
    <main class="container">
      <div class="row">
        <Card
        v-for="(element, index) in store.cardList"
        :cardImg="element.card_images[0].image_url_small"
        :cardName="element.name"
        :cardArchetype="element.archetype"
        />
      </div>
    </main>
  </div>
</template>

<script>
  import { store } from './data/store';
  import axios from 'axios';
  import Card from './components/Card.vue';

  export default {
    components: {
      Card
    },
    data() {
      return {
        store
      }
    },
    methods: {
      getCards(){
        const url = store.apiUrl;
        axios.get(url).then((response) =>{
          console.log(response.data.data);
          store.cardList = response.data.data;
        })
      }
    },
    created(){
      this.getCards()
    }
  }
</script>

<style lang="scss" scoped>

</style>