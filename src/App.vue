<template>
  <div class="bg-main">
    <HeaderComponent />
    <div class="container py-4">
      <select class="p-2 w-25 rounded-3" aria-label="Default select example">
        <option selected>Alien</option>
      </select>
    </div>
    
    <div class="container bg-light padding-found-cards">
      <h6 class="m-0 text-light bg-dark p-4 fw-bold">Found {{ store.cardList.length }} cards</h6>
    </div>
    <main class="container">
      <div class="row bg-light padding-cards">
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
  import HeaderComponent from './components/HeaderComponent.vue';
  import Card from './components/Card.vue';

  export default {
    components: {
      Card,
      HeaderComponent
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
  .padding-found-cards {
    padding: 60px 60px 0 60px;
  }
  .padding-cards {
    padding: 0 48px 0 48px;
  }
</style>