<template>
    <div>
        <input v-model="text" type="text">
        {{text}}
    </div>
</template>
<script>
export default {
    name:"Add",
    data(){
        return{
           text:"" 
        }
    }
}
</script>
<style lang="">
    
</style>