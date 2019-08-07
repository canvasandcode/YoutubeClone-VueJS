<template>
    <div>
        <!--listens for termChange event to be emitted from searchbar, then runs function-->
        <SearchBar @termChange="onTermChange"></SearchBar>
        <VideoList></VideoList>
    </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';

const API_KEY = 'AIzaSyCm3jr9B1jvJ87taITzUsHGXw9vEMKIAUw'; //using caps here as its const, to make more clear

export default {
    //helps identify when debugging in browser
    name: 'App', 
    components: {
        SearchBar,
        VideoList
    },
    methods: {
        //searchTerm is 2nd arg from searchbar.vue file, passed the users input through this
        onTermChange(searchTerm) { 
            //and log it here
            // console.log(searchTerm); 

            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            }).then(response => console.log(response));
        }
    }
};
</script>

<style>

</style>

