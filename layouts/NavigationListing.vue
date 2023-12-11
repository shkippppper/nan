<template lang="pug">
.listing
    h1 MEM2
    .listing-wrapper
        .work.in
            span(@click="workOpen=!workOpen") work
            .work-wrapper(v-show="workOpen")
                .public.inner
                    span(@click="publicOpen=!publicOpen") public
                    .links(v-show="publicOpen")
                        router-link(:to="{name: 'work-public-slug', params:{slug: 'rectangle'} }" :style="{textDecoration: workOpen ? 'underline' : 'initial'}") text
                        a text
                        a text
                        a text
                        a text
                        a text
                        a text
                .office.inner
                    span(@click="officeOpen=!officeOpen") office
                    .links(v-show="officeOpen")
                        a text
                        a text
                        a text
                .housing.inner
                    span(@click="housingOpen=!housingOpen") housing
                    .links(v-show="housingOpen")
                        a text
                        a text
                        a text
        .studio.in
            span(@click="studioOpen=!studioOpen") studio
            .links(v-show="studioOpen")
                a contact
                a profile
                a awards
                a exhibitions
                a publications

</template>

<script>
export default {
    name: 'NavigationListing',
    data() {
        return {
            workOpen: false,
            publicOpen: false,
            officeOpen: false,
            housingOpen: false,
            studioOpen: false,
        }
    },
}
</script>

<style scoped>

.inner,
.in,
.links {
    display: flex;
    flex-direction: column;
    margin-left: 10px;
}

span:hover,
a:hover {
    text-decoration: underline;
    cursor: pointer;
}

span.active,
a.active {
    text-decoration: underline;
}

.links a{
    color: initial;
}

li:hover {
    text-decoration: underline;
}


.listing {
    width: 240px;
    height: 100%;
    float: left;
    padding-left: 20px;
    position: fixed;
}

h1 {
    padding-left: 10px;
    font-size: 16px;
    line-height: 24px;
    font-weight: 600;
    margin: 40px 0 30px;
}

</style>
