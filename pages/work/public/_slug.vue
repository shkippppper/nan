<template lang="pug">
.image-wrapper
    img(:src="testImage")
</template>

<script>
import testImage from "../../../content/images/test_image.jpg"
export default {
    name: 'IndexPage',
    data(){
        return{
            testImage: testImage
        }
    },
    mounted() {

        let formData = {
            a : 'aaa'
        }
        fetch("https://mem2-f7aea-default-rtdb.europe-west1.firebasedatabase.app/memdata", {
            method: "POST",
            headers: {
                'Content-type' : 'application/json'
            },
            body: formData,
        });
    }
}
</script>

<style>
.image-wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 50px 50px 50px 260px; /* Adjust padding as needed */
    overflow: hidden; /* Prevents scroll if the image is too big */
    height: 100vh; /* Full viewport height */
    width: 100vw; /* Full viewport width */
    box-sizing: border-box; /* Ensures padding is included in width/height */
}

img {
    max-width: 100%; /* Maximum width is 100% of the parent */
    max-height: 100%; /* Maximum height is 100% of the parent */
    width: auto; /* Maintain aspect ratio */
    height: auto; /* Maintain aspect ratio */
    object-fit: cover; /* Cover the container without distorting */
}

@media screen and (max-width: 749px){
    .image-wrapper {
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 50px 50px 50px 50px; /* Adjust padding as needed */
        overflow: hidden; /* Prevents scroll if the image is too big */
        height: 100vh; /* Full viewport height */
        width: 100vw; /* Full viewport width */
        box-sizing: border-box; /* Ensures padding is included in width/height */
    }
}

</style>

