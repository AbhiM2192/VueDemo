<template>
    <div>
        <h2>Component D</h2>
        <ComponentE/>
    </div>
</template>

<script>

import ComponentE from './ComponentE'
    export default {
        name:'ComponentD',
        components:{ComponentE}
    }
</script>

<style scoped>

</style>