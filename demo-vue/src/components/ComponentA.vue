<template>
     <div>
         <h2>{{name}}</h2>
         <div>
             <button @click="changeName(),increment()">Change Name</button>
        </div>
        <h2>{{count}}</h2>
        <div><button @click="increment">Increment</button></div>
        <div><button v-on:click="decrement(1,$event)">Decrement</button></div>
    </div>
</template>
<script>
    export default {
        name:'componentA',
        data(){
            return{
                name:'I am Component A',
                count:0
            }
        },
        methods:{
            changeName(){
                this.name = 'Batman'
            },
            increment(ev){
                this.count += 1
                console.log('Event',ev)
            },
            decrement(num,ev){
                this.count === 0 ? this.count = 0 : this.count -=num
                console.log('Event',ev)
            }
        }
    }
</script>
<style></style>