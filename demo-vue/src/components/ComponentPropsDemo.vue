<template>
    <div>
        <h2>Hello {{name}}</h2>
    </div>
</template>

<script>
    export default {
        name:'ComponentPropsDemo',
        data(){
            return{
                fullName:'AB'
            }
        },
        props:['name']
    }
</script>

<style scoped>

</style>