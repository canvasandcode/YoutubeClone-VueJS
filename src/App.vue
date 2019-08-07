<template>
  <div>
    <!--listens for termChange event to be emitted from searchbar, then runs function-->
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoList></VideoList>
    {{ videos.length }}
    <!--retrieve length from videos data property-->
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";

const API_KEY = "AIzaSyCm3jr9B1jvJ87taITzUsHGXw9vEMKIAUw"; //using caps here as its const, to make more clear

export default {
  //helps identify when debugging in browser
  name: "App",
  components: {
    SearchBar,
    VideoList
  },
  data() {
    //have to use a function that returns a data property as we are in a component
    return { videos: [] };
  },
  methods: {
    //searchTerm is 2nd arg from searchbar.vue file, passed the users input through this
    onTermChange(searchTerm) {
      //and log it here
      // console.log(searchTerm);

      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm
          }
        })
        .then(response => {
          this.videos = response.data.items; //this is the data property that is tied to response from youtube, not our instance
        });
    }
  }
};
</script>

<style>
</style>

