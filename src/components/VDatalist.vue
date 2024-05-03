<script setup>
import { ref, onBeforeUpdate } from 'vue';


    const props = defineProps({
        search: {
            type: String,
            default: 'Car',
        }
    })
    
    let searchSuggestions  = ref([]);

    const getData = async() => {
        try{
        const res = await fetch(`https://api.addsearch.com/v1/suggest/1bed1ffde465fddba2a53ad3ce69e6c2?term=${props.search}`).then(result => {return result.json()})

        searchSuggestions.value = res.suggestions
        }catch(error){
            console.error(error);
        }
    }

    getData();

    onBeforeUpdate(() => getData());
    
</script>

<template>
    <div class="suggestions">
        <span :value="suggestions" v-for="suggestions in searchSuggestions">{{ suggestions.value }}</span>
    </div>
</template>

<style scoped>
    .suggestions{
        display: flex;
        flex-flow: column;
        justify-content: center;
        width: 92%;
        background-color: #FFF;
        border-bottom-left-radius: 10px;
        border-bottom-right-radius: 10px;
        gap: 10px;
    }

    .suggestions > span{
        width: 100%;
        height: 30px;
        text-align: center;
        font-size: 24px;
        font-family: Inter;
        font-weight: 400;
        line-height: 29.05px;
        color: #5C6B73;
    }

    .suggestions > span:hover{
        background-color: #BCA3FF33;
        cursor: pointer;
    }
</style>