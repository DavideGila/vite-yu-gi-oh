<template>
    <div class="container py-4">
      <select class="p-2 w-25 rounded-3" aria-label="Default select example" v-model="filterStatus" @change="$emit('search', filterStatus)">
        <option value="">All</option>
        <option value="alien">Alien</option>
        <option value="infernoble-arms">Infernoble Arms</option>
        <option value="noble-knight">Noble Knight</option>
        <option value="melodious">Melodious</option>
        <option value="archfiend">Archfiend</option>
      </select>
    </div>
</template>

<script>
    export default {
        name:'SearchComponent',
        data() {
            return {
                filterStatus: ''
            }
        },
    }
</script>

<style lang="scss">

</style>