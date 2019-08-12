<template>
    <div>
        <input type="text" v-on:input="onInput">
        
    </div>
</template>

<script>
export default {
    name: 'SearchBar',
    methods: {
        onInput: function(event) {
            this.$emit('termChange', event.target.value); //2nd value here, but first arg in app.vue (SearchTerm)
        }
    }

}
</script>

<style scoped>
    input {
        width: 75%
    } 
    
    div {
        text-align: center;
        margin: 20px;
    }
</style>
