<template>
    <div class="image_list">
        <div v-for="image in images" :key="image.id">
            <img width="250" height="250" :src="image.urls.regular" :alt="image.alt_description" />
        </div>

    </div>
    <ul class="pagination">
        <li v-for="page in totalPages" :key="page" @click="changePage(page)" class="page" :class="{ active: currentPage === page }">
            {{ page }}</li>
    </ul>
</template>
  
<script>
import axios from 'axios';

export default {
    data() {
        return {
            accesskey: process.env.VUE_APP_UNSPLASH_ACCESS_KEY,
            images: [],
            currentPage: 1,
            totalPages: 3,
            imagesPerPage: 10,
        };
    },
    mounted() {
        this.fetchImages();
    },
    methods: {
        async fetchImages() {
            const response = await axios.get(`https://api.unsplash.com/photos?page=${this.currentPage}&per_page=${this.imagesPerPage}&client_id=${this.accesskey}`);
            this.images = response.data;
        },
        changePage(page) {
            this.currentPage = page;
            this.fetchImages();
        },
    },
};
</script>
<style scoped lang="scss">
.image_list {
    display: flex;
    flex-wrap: wrap;
    gap: 5px;
    div{
        
    }
}
.pagination{
    display: flex;
    width: 100%;
    align-items: center;
    justify-content: center;
    gap: 15px;
    .page{
        display: flex;
        background-color: teal;
        align-items: center;
        justify-content: center;
        border-radius: 6px;
        width: 30px;
        height: 30px;
        cursor: pointer;
        transition: all .3s ease;
        &:hover{
            background-color: #04598b;
        }
    }
    .active{
        background-color: #0093e8;
    }
}
</style>
  