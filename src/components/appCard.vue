<script>
export default{
    name:'appCard',
    props:{
        movie:Object
    },
    computed:{
            flag(){
                let lang=this.movie.original_language;
                switch(lang){
                    case 'en':
                        lang='uk';
                        break;
                        case 'pt':
                            lang='po';
                            break;
                            case 'es':
                            lang= 'sp';
                            break;
                }
                const flag=`https://www.worldometers.info//img/flags/small/tn_${lang}-flag.gif`;
                return flag;
            }


            
        } , 
        methods:{
           getCover(){
            const baseCoverUrl ='https://image.tmdb.org/t/p/';
            const coverSize = 'w342';
            const posterPath=  this.movie.poster_path;
            return baseCoverUrl + coverSize + posterPath;
           },
           getVote(){
             let newVote= this.movie.vote_average;
             newVote= newVote / 2;
             newVote= Math.ceil(newVote);
             return newVote
           }

        }  
}
</script>

<template>
    <div >
        <img :src="getCover()">
        <h3>{{ movie.title || movie.name}}</h3>
        <h4>{{ movie.original_language || movie.original_name }}</h4>
        <p>{{ movie.original_language }}</p>
        <img :src="flag">
        <div>
            <span v-for="n in getVote()">★</span>
            <span v-for="n in (5 - getVote())">☆</span>
        </div>
    </div> 
</template>