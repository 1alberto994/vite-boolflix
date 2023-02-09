<script >
import axios from 'axios';
import {store} from './store';
import appHeader from './components/appHeader.vue';
import appMain from './components/appMain.vue';
export default{
  name:"App",
  data(){
    return{
      store
    }
  },
  methods:{
            fullMovieAndSeries(){
                let url='https://api.themoviedb.org/3/search/movie';
                axios
                    .get(url + 'movie', {
                        params: {
                            api_key:'adac4cd106eb6249d7ed7d814230e785',
                            query:this.store.searchText,
                            language:'it-IT'
                        
                        }
                    })
                    .then((response) => {
                        this.store.movies = response.data.results;
                        
                    });
            }
        },
  components:{
    appHeader,
    appMain
  }
}
</script>

<template>
  <appHeader @search="fullMovieAndSeries"/>
  <appMain/>
</template>

<style scoped>

</style>
