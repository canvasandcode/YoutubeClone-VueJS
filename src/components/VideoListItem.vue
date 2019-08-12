<template>
  <li class="list-group-item media" @click="onVideoSelect">
    <!--getting thumbnails from computed property-->
    <img :src="thumbnailUrl" :alt="videoTitle" class="mr-3" />
    <div class="media-body">
      <h3>{{videoTitle}}</h3>
      <!--name of video)-->
    </div>
  </li>
</template>

<script>
export default {
  //expect to get a property from parent (VideoList) called 'video'
  name: "VideoListItem",
  props: ["video"],
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
    videoTitle() {
      return this.video.snippet.title;
    }
  },
  methods: {
    onVideoSelect() {
        this.$emit('videoSelect', this.video);
    }
    
  }
};
</script>

<style scoped>
li {
  display: flex;
  cursor: pointer;
  transition: all 0.4s;
}

li:hover {
  background-color: #eee;
}
</style>


<!--removed style tag as nothing will really be styled here-->