<template>
    <ul class="list-group">
        <!--'video' acts as a temporary variable that is available only inside template, no property called video exists- video in bind speechmarks has to match name-->
        <!--v-for creates multuple instances of video list item-->
        <VideoListItem 
            v-for="video in videos" 
            :video="video"
            :key="video.etag"
            @videoSelect="onVideoSelect">
            <!-- :video="same name from v-for first variable" -->
        </VideoListItem>
        <!-- {{videos.length}} print out the number of videos that has been passed down as props from App.vue -->
    </ul>
</template>

<script>
import VideoListItem from './VideoListItem';

export default {
    name: 'VideoList',
    components: {
        VideoListItem
    },
    props: {
        //'videos' has to be called the same as how it is in parent component
        videos: Array // telling component that it will receive a prop called 'videos' and TYPE has to be an Array otherwise will throw an error
    },
    methods: {
        onVideoSelect(video) {
            this.$emit('videoSelect', video);
        }
    } 
};
</script>

<style scoped>

</style>

