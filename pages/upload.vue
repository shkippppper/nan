<template lang="pug">
div
    form(@submit.prevent="updateJSON")
        input(type="file" @change="handleFileChange" accept="image/*")
        input(type="text" v-model="description" placeholder="Enter description" required)
        button(type="submit") Update JSON
    div(v-if="imageData")
        img(:src="imageData" alt="Uploaded image")
        p {{ slug }}
</template>

<script>
export default {
    data() {
        return {
            description: '',
            imageData: null,
            slug: '',
            existingData: {},
        };
    },
    mounted() {
        this.loadExistingData();
    },
    methods: {
        loadExistingData() {
            fetch('data.json')
                .then(response => {
                    console.log(response)
                    if (!response.ok) {
                        throw new Error('Network response was not ok');
                    }
                    return response.json();
                })
                .then(data => {
                    this.existingData = data;
                })
                .catch(error => {
                    console.error('Error loading existing data:', error);
                });
        },
        handleFileChange(event) {
            const file = event.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = (e) => {
                    this.imageData = e.target.result;
                };
                reader.readAsDataURL(file);
            }
        },
        generateSlug() {
            return this.description
                .toLowerCase()
                .replace(/ /g, '-')
                .replace(/[^\w-]+/g, '');
        },
        updateJSON() {
            this.slug = this.generateSlug();
            const newEntry = {
                description: this.description,
                slug: this.slug,
                image: this.imageData,
            };

            this.existingData[this.slug] = newEntry;

            const blob = new Blob([JSON.stringify(this.existingData)], { type: 'application/json' });
            const url = URL.createObjectURL(blob);

            const a = document.createElement('a');
            a.href = url;
            a.download = 'data.json';
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);

            URL.revokeObjectURL(url);
        },
    },
};
</script>

<style scoped>
/* Add your styles here */
</style>
