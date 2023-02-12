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
               this.makeSearch('movie');
               this.makeSearch('tv')
            },
            makeSearch(enpoint){
              let url='https://api.themoviedb.org/3/search/';
                axios
                    .get(url + enpoint, {
                        params: {
                            api_key:'e99307154c6dfb0b4750f6603256716d',
                            query:this.store.searchText,
                            language:'it-IT',
                        
                        }
                    })
                    .then((response) => {
                        if(enpoint=='movie'){
                          this.store.movies=response.data.results;
                        }
                        else{
                          this.store.series=response.data.results;
                        }
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
