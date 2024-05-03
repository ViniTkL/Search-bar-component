<script setup>
    import { ref } from 'vue';
    import VDatalist from './VDatalist.vue';
    
    let search = ref('')
</script>

<template>
    <div class="search-container">
        <form role="search" action="" class="search-form">
            <input type="search" class="search-input" name="q" id="search-bar" placeholder="Search..." minlength="1" list="suggestions" v-model="search"/> 
            <button class="search-btn">Go</button>
        </form>
        <VDatalist :search="search"/>
    </div>
</template>

<style scoped>
.search-container{
    display: flex;
    flex-flow: column;
    justify-content: center;
    width: 600px;
    gap: 10px;
}
.search-form{
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
}

.search-input{
    width: 100%;
    height: 50px;
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
    border: 1px solid #FFF;
    padding: 5px 10px 5px 10px;
    font-size: 20px;
    font-size: 24px;
    font-weight: 400;
    line-height: 29.05px;
    color: #5C6B73;
}

.search-input:focus{
    outline: none;
}

.search-btn{
    position: relative;;
    height: 50px;
    width: 10%;
    border-top-left-radius: 15px;
    border-top-right-radius: 15px;
    border-bottom-left-radius: 15px;
    border: none;
    background-color: #D8BFD8;
    right: 45px;
    font-size: 20px;
    color: #FFF;
    cursor: pointer;
}


</style>