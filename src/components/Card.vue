<template>
   <div class="col-2 pb-3 bg-light">
        <div>
            <img :src="cardImg" :alt="cardName" class="w-100"/>
            <div class="text-center bg-cards h">
                <h6 class="title text-light text-uppercase fs-5">{{ cardName }}</h6>
                <p>{{ cardArchetype }}</p>
            </div>
        </div>
    </div>
</template>

<script>
import { store } from '../data/store'

    export default {
        name: 'Card',
        props: {
            cardImg: String,
            cardName: String,
            cardArchetype: String
        },
        data() {
            return {
                store
            }
        },
    }
</script>

<style lang="scss">
    .bg-cards{
        background-color: #D48F38;
    }
    .h {
        height: 150px
    }
</style>