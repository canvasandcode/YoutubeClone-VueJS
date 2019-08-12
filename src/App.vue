<template>
  <div class="container">
    <!--listens for termChange event to be emitted from searchbar.vue file, then runs method below-->
    <SearchBar @termChange="onTermChange"></SearchBar>
    <!--SearchBar emits an event called termchange-->

    <VideoDetail :video="selectedVideo" />

    <VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
    <!--inside the VideoList we will have access to a property called videos, name in speech marks should match the empty array in data prop below-->
    
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VideoDetail";

const API_KEY = "AIzaSyBbrNzW1HuqCFwVzz9dMYnc-sh2jooUOuE"; //using caps here as its const, to make more clear

export default {
  //helps identify when debugging in browser
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    //have to use a function that returns a data property as we are in a component not an instance
    return { 
      videos: [],
      selectedVideo: null }; //initialise as empty array
  },
  methods: {
    onVideoSelect(video) {
      this.selectedVideo = video;
    },
    //searchTerm is 2nd arg from searchbar.vue file, passed the users input text through this
    onTermChange(searchTerm) {
      //and log it here
      // console.log(searchTerm);

      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm //q is for query, searchTerm is the users input from SearchBar.vue
          }
        })
        .then(response => {
          //fill the empty array from above with the data from API
          this.videos = response.data.items; //THIS data property that is tied to response from youtube, not our instance
        });
    }
  }
};
</script>

<style>
</style>

