<template>
  <div class="bg-main">
    <HeaderComponent />
    <SearchComponent @search="setParams" />   
    <div class="container bg-light padding-found-cards">
      <h6 class="m-0 text-light bg-dark p-4 fw-bold">Found {{ store.cardList.length }} cards</h6>
    </div>
    <main class="container">
      <div class="row bg-light padding-cards">
        <Card
        v-for="(element, index) in store.cardList"
        :cardImg="element.card_images[0].image_url"
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
  import SearchComponent from './components/SearchComponent.vue';

  export default {
    components: {
      Card,
      HeaderComponent,
      SearchComponent
    },
    data() {
      return {
        store,
        params: null
      }
    },
    methods: {
      setParams(search){
        console.log(search);
        this.params = {
          archetype: search
        }
        this.getCards()
      },
      getCards(){
        const url = store.apiUrl;
        axios.get(url, {params: this.params}).then((response) =>{
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