<template>
    <div class="search-box">
        <input class="search-text" type="text" placeholder="Search" v-model="keywordSearch" @keyup.enter="$emit('search', keywordSearch)">
        <button  class="search-button" @click="$emit('search', keywordSearch)">Search</button>
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
.search-box{
    margin-right: 20px;
    .search-text{
        padding: 10px;
        border: 0px;
        border-radius: 10px;
        margin-right: 10px;
    }
    .search-button{
        padding: 10px;
        border: 0px;
        border-radius: 10px;
        background-color: #555;
        color: #fff;
        cursor: pointer;
    }
}
</style>