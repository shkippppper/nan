<template lang="pug">
.wrapper
    NavigationListing
</template>

<script>
import Vue from 'vue'
import NavigationListing from '../components/NavigationListing.vue'

export default Vue.extend({
    name: 'IndexPage',
    components: {
        NavigationListing
    }
})
</script>

<style>
*{
    margin: 0;
    padding: 0;
    font-family: 'arial', sans-serif;

    letter-spacing: 1px;
    text-transform: uppercase;
    font-size: 10px;
    line-height: 20px;
    font-weight: 200;
}
</style>
