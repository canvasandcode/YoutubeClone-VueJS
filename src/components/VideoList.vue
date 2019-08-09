<template>
    <ul>
        VideoList
        {{videos.length}}
    </ul>
</template>

<script>
export default {
    name: 'VideoList',
    props: {
        //'videos' has to be called the same as how it is in parent component
        videos: Array // telling comp that will receive a prop called videos and expect it to be an array
    } 
};
</script>

<style>

</style>
