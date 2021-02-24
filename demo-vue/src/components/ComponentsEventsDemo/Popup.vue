<template>
    <div>
        <h2>This is a Popup</h2>
        <button @click="$emit('closePopup','Data from PopupComponent')">Close Popup</button>
    </div>
</template>

<script>
    export default {
        name:'Popup',
        emits:['closePopup']
    }
</script>

<style scoped>

</style>