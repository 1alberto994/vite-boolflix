<script>
    import { store } from '../store.js';
    import appCard from './appCard.vue'
     export default{
        name:'appMain',
        data(){
            return{
                store
            }
        },
        
           
            
        
        components:{
            appCard
        }
     }      
</script>

<template>

    <main >
        <appCard v-for="movie in store.movies"
         :movie="movie"
        />
        <appCard v-for="singleSeries in store.series"
         :movie="singleSeries"
        />
       

    </main>

</template>