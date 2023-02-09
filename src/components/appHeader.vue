<script>
    import { store } from '../store.js';
    export default{
        name:'appHeader',
        data(){
            return{
                store
            }
        },
        
    }  
</script>
<template>

    <header>

        <div v-for="movie in store.movies">
           <input type="text" placeholder="inserisci un film o una serie tv" v-model=store.searchText >
            <button @click="$emit('search')">
             Search
            </button>
        </div>
       

    </header>

</template>