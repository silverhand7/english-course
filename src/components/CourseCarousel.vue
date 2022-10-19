<template>
    <Carousel :items-to-show="1" ref="myCarousel">

        <Slide v-for="material in materials" :key="material.id">
            <FlipCard v-if="material.type === 'course'" :name="material.name" :meaning="material.meaning" :example="material.example" />

            <QuizCard
                v-if="material.type === 'quiz'"
                :question="material.question"
                :answers="material.answers"
                @clickedAnswer="calculate"
            />
        </Slide>

        <template #addons>
            <pagination />
        </template>
    </Carousel>
</template>

<script>
import FlipCard from '@/components/FlipCard.vue';
import QuizCard from '@/components/QuizCard.vue';
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'

export default {
    components: {
        FlipCard,
        QuizCard,
        Carousel,
        Slide,
        Pagination,
        Navigation,
        QuizCard
    },
    data() {
        return {
            correctAnswer: 0,
        }
    },
    props: {
        materials: {
            required: true,
            type: Array
        }
    },
    methods: {
        calculate(data) {
            if(data.isCorrect) {
                this.correctAnswer++;
            }
            console.log(this.correctAnswer);
        }
    }

}
</script>

<style>
ol.carousel__track {
    margin: 40px 0;
}
ol.carousel__pagination {
    padding-left: 0;
}
</style>