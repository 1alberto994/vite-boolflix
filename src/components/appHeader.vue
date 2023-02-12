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

        <div >
            <h1>BOOLFLIX</h1>
           <input type="text" placeholder="inserisci un film o una serie tv" v-model=store.searchText >
            <button @click="$emit('search')">
             Search
            </button>
        </div>
       

    </header>

</template>