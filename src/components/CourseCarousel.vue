<template>
    <Carousel v-if="!showScore" :items-to-show="1">
        <Slide v-for="material in materials" :key="material.id">
            <FlipCard
                v-if="material.type === 'course'"
                :number="material.id"
                :name="material.name"
                :meaning="material.meaning"
                :example="material.example"
            />

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
    <div v-else class="score bg-white p-4 text-center d-flex align-items-center justify-content-center">
        <div>
            <p>Congratulations! 🎉</p>
            <p>Your Score is</p>
            <h1>{{ score }}</h1>

            <p>Thanks for finishing the course!</p>
        </div>
    </div>
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
            totalAnswered: 0,
            showScore: false,
            score: 0,
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
            this.totalAnswered++;
            if(data.isCorrect) {
                this.correctAnswer++;
            }

            const totalQuiz = this.materials.filter(t => t.type == 'quiz').length;
            if (totalQuiz === this.totalAnswered) {
                setTimeout(() => {
                   this.showScore = true;
                   this.score = (totalQuiz - (totalQuiz - this.correctAnswer)) / totalQuiz;
                   this.score *= 100;
                   this.score = parseInt(this.score);
                }, 1500);
            }
        }
    },

}
</script>

<style>
.score {
    width: 300px;
    border-radius: 15px;
    height: 500px;
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
    margin:40px auto;
}
ol.carousel__track {
    margin: 40px 0;
}
ol.carousel__pagination {
    padding-left: 0;
}
</style>