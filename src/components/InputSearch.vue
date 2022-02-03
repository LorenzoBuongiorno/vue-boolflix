<template>
    <div>
        <input type="text" placeholder="Search" v-model="keywordSearch" @keyup.enter="$emit('search', keywordSearch)">
        <button  class="search" @click="$emit('search', keywordSearch)">Search</button>
    </div>
</template>

<script>
export default {
    data (){
        return {
            keywordSearch: ''
        }
    }
}
</script>

<style lang="scss">

</style>