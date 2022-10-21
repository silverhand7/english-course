<template>
    <div v-if="!showScore" >
        <Carousel :items-to-show="1" v-model="currentSlide">
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
                <div>
                    <div class="carousel__prev"
                        :class="{'carousel__prev--disabled': currentSlide == 0}"
                        @click="prev"
                    >
                        <svg class="carousel__icon" viewBox="0 0 24 24" role="img" ariaLabel="arrowLeft"><title>arrowLeft</title><path d="M15.41 16.59L10.83 12l4.58-4.59L14 6l-6 6 6 6 1.41-1.41z"></path></svg>
                    </div>
                    <div class="carousel__next"
                        :class="{'carousel__next--disabled': currentSlide == materials.length - 1}"
                        @click="next"
                    >
                        <svg class="carousel__icon" viewBox="0 0 24 24" role="img" ariaLabel="arrowRight"><title>arrowRight</title><path d="M8.59 16.59L13.17 12 8.59 7.41 10 6l6 6-6 6-1.41-1.41z"></path></svg>
                    </div>
                </div>
            </Slide>
        </Carousel>
        <div class="progress progress-bar-customize">
            <div class="progress-bar" role="progressbar"
                :style="{ 'width': progress + '%' }"
                aria-valuemax="100">
            </div>
        </div>
    </div>

    <div v-else class="score bg-blurry p-4 text-center text-white d-flex align-items-center justify-content-center">
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
        QuizCard,
        Navigation
    },
    data() {
        return {
            correctAnswer: 0,
            totalAnswered: 0,
            showScore: false,
            score: 0,
            currentSlide: 0,
            progress: 0,
        }
    },
    computed: {
        totalSlides() {
            return this.materials.length;
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
        },
        next() {
            this.currentSlide += 1;
            this.progress = (this.currentSlide / (this.totalSlides - 1)) * 100;
        },
        prev() {
            this.currentSlide -= 1;
            this.progress = (this.currentSlide / (this.totalSlides - 1)) * 100;
        },
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

.carousel__prev, .carousel__next {
    background-image: url(/src/assets/images/arrow-bg.png) !important;
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    width: 45px;
    height: 65px;
    color: white;
}

.carousel__prev:hover, .carousel__next:hover {
    color: white;
}

.progress-bar-customize {
    height: 8px;
    background: #385682;
    border-radius: 120px;
}

.progress-bar-customize .progress-bar {
    background: #A8F68C;
}
</style>