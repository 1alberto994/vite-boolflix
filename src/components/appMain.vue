<script>
    import { store } from '../store.js';
     export default{
        name:'appMain',
        data(){
            return{
                store
            }
        }
     }      
</script>

<template>

    <main >
       <div v-for="movie in store.movies">
        <h3>{{ movie.title }}</h3>
        <h4>
            {{ movie.original_title }}
        </h4>
        <h5>{{ movie.original_language }}</h5>
       </div> 
    </main>

</template>