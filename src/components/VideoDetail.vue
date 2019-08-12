<template>
    <div v-if="video">
        {{ video.snippet.title }}
    </div>
</template>

<script>
export default {
    name: "VideoDetail",
    props: {
        //the selected video
        video: Array  
    }
}
</script>

<style>

</style>
