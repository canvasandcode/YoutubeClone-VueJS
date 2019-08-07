<template>
    <div>
        <SearchBar></SearchBar>
    </div>
</template>

<script>
import SearchBar from './components/SearchBar';

export default {
    
    name: 'App', //helps identify when debugging in browser
    components: {
        SearchBar: SearchBar
    }
};
</script>

<style>

</style>

