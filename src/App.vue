<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar> <!--listens for termChange event to be emitted from searchbar, then runs function-->
    </div>
</template>

<script>
import SearchBar from './components/SearchBar';

export default {
    
    name: 'App', //helps identify when debugging in browser
    components: {
        SearchBar
    },
    methods: {
        onTermChange(searchTerm) { //searchTerm is 2nd arg from searchbar.vue file, passed the users input through this
            console.log(searchTerm); //and log it here
        }
    }
};
</script>

<style>

</style>

