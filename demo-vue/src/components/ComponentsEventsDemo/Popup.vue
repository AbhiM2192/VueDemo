<template>
    <div>
        <h2>This is a Popup</h2>
        <input type="text" v-model="name">
        <button @click="$emit('closePopup',name)">Close Popup</button>
    </div>
</template>

<script>
    export default {
        name:'Popup',
        emits:{
            closePopup: (name) =>{
                if(!name){
                    return false
                } else {
                    return true
                }
            }
        },
        data(){
            return{
                name:''
            }
        }
    }
</script>

<style scoped>

</style>