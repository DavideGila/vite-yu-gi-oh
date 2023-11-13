<template>
   <div class="col-2 py-5">
        <div>
            <img :src="cardImg" :alt="cardName" class="w-100"/>
            <div>
                <h6 class="title">{{ cardName }}</h6>
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

<style lang="scss" scoped>

</style>