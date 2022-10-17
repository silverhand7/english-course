<template>
    <div class="mt-5"></div>
    <carousel class="mt-5" :items-to-show="1">
        <Slide v-for="slide in slides" :key="slide.id">
            <FlipCard :name="slide.name" :meaning="slide.meaning" :example="slide.example" />
        </Slide>

        <template #addons>
            <pagination />
        </template>
    </carousel>
</template>

<script>
import FlipCard from '@/components/FlipCard.vue';
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'

export default {
    components: {
        FlipCard,
        Carousel,
        Slide,
        Pagination,
        Navigation,
    },
    props: {
        slides: {
            required: true,
            type: Array
        }
    }
}
</script>

<style>
ol.carousel__track {
    margin: 40px 0;
}
ol.carousel__pagination {
    margin-top:40px;
    padding-left: 0;
}
</style>