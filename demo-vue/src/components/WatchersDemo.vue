<template>
    <div>
        <h2>Volume Tracker (0-20)</h2>
        <h3>Current Volume - {{volume}}</h3>
        <div>
            <button @click="volume += 2">Increase</button>
            <button @click="volume -= 2">Decrease</button>
        </div>
        <input type="text" v-model="movie">
        <input type="text" v-model="movieInfo.title">
        <input type="text" v-model="movieInfo.actor">
        <div>
            <button @click="movieList.push('The Shawshank Redemption')">Add Movie</button>
        </div>
    </div>
</template>

<script>
export default {
    name:'WatchersDemo',
    data(){
        return{
            volume:0,
            movie:'abhi',
            movieInfo:{
                title:'',
                actor:''
            },
            movieList:['The Dark Knight rises','Avengers']
        }
    },
    methods:{},
    computed:{},
    watch:{
        volume(newValue,oldValue){
            if(newValue > oldValue && newValue == 16){
                console.log('High Volume')
            }
        },
        movie:{
            handler(newValue){
            console.log(`Calling API with Movie Name ${newValue}`)
            },
            immediate:true, 
        },
        movieInfo:{
            handler(newValue){
                console.log(`Calling API with movie Title = ${newValue.title} and actor = ${newValue.actor}`)
            },
            deep:true
        },
        movieList:{
            handler(newValue){
                console.log(`Updated List is ${newValue}`)
            },
            deep:true
        }
    }
}
</script>