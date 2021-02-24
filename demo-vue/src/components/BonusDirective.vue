<template>
    <h2 v-once>{{name}}</h2>
    <button @click="name = 'IronMan'">Change Name</button>
    <h2 v-pre>{{name}}</h2>
</template>

<script>
export default {
    name:'bonusD',
    data(){
        return{
            name:'Abhishek'
        }
    }
}

//v-once : Skips any change on element after first render. Basically tells vue not to run any diffing algorithm after initial render.
//v-pre : tells the vue compiler to render the template as is without recognising any vue related code.
</script>