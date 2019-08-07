<template>
    <div>
        <!--listens for termChange event to be emitted from searchbar, then runs function-->
        <SearchBar @termChange="onTermChange"></SearchBar>
    </div>
</template>

<script>
import SearchBar from './components/SearchBar';
const API_KEY = 'AIzaSyCm3jr9B1jvJ87taITzUsHGXw9vEMKIAUw'; //using caps here as its const, to make more clear

export default {
    //helps identify when debugging in browser
    name: 'App', 
    components: {
        SearchBar
    },
    methods: {
        //searchTerm is 2nd arg from searchbar.vue file, passed the users input through this
        onTermChange(searchTerm) { 
            //and log it here
            console.log(searchTerm); 
        }
    }
};
</script>

<style>

</style>

