<template>
    <li>
        {{video.snippet.title}} <!--name of video)-->
    </li>
</template>

<script>
export default {
    name: 'VideoListItem',
    props: ['video'] //expect to get a property from parent called video 
}
</script>

<!--removed style tag as nothing will really be styled here-->