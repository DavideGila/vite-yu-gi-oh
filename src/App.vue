<template>
  <div class="bg-main">
    <!-- <HeaderComponent title="Yu-Gi-Oh Api"/> -->
    <div class="container bg-light">
      <h6 class="m-0 text-light bg-dark p-4 fw-bold">Found {{ store.cardList.length }} cards</h6>
    </div>
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

<style lang="scss">
  .bg-main{
    background-color: #D48F38;
  }

</style>