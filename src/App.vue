<template>
  <div>
    <!-- <HeaderComponent title="Yu-Gi-Oh Api"/> -->
    <main class="container">
      <div class="row">
        <!-- <CardComponent/> -->
      </div>
    </main>
  </div>
</template>

<script>
  import { store } from './data/store'
  import axios from 'axios';

  export default {
    data() {
      return {
        store
      }
    },
    methods: {
      getCards(){
        const url = store.apiUrl;
        axios.get(url).then((response) =>{
          console.log(response.data);
          store.cardList = response.data;
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