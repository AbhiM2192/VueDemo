<template>
    <div>
        <h3 v-for="name in names " :key="name.fName">
            {{name.fName}} || {{name.lName}}
        </h3>
    </div>
</template>

<script>
    export default {
        name:'SlotPropsDemo',
        data(){
            return {
                names:[
                    {fName:'Bruce',lName:'Wayne'},
                    {fName:'Tony',lName:'Stark'},
                    {fName:'Dr.',lName:'Strange'}
                ]
            }
        }
    }
</script>

<style scoped>

</style>