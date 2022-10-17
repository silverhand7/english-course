<template>
    <CourseCarousel :slides="slides" />
</template>

<script>
import CourseCarousel from '@/components/CourseCarousel.vue';

export default {
    components: {
        CourseCarousel
    },
    data() {
        return {
            slides: [
                {
                    id: 1,
                    type: 'course',
                    name: 'A storm in a teacup',
                    meaning: 'a lot of unnecessary anger and worry about a matter that is not important',
                    example: 'She’s made an official complaint to the CEO about the type of cheese in the cheese sandwiches at the canteen. This seems to me to be a storm in a teacup.'
                },
                {
                    id: 2,
                    type: 'course',
                    name: 'Bob’s your uncle!',
                    meaning: '"and there it is" or "and there you have it"',
                    example: 'To make a cup of mint tea; boil a kettle, add a tea bag, wait 2 minutes and Bob\'s your uncle!'
                },
                {
                    id: 3,
                    type: 'quiz',
                    question: 'What is Bob\'s your uncle means?',
                    answers: [
                        {
                            answer: 'There you have it/ there it is',
                            isTrue: true,
                        },
                        {
                            answer: 'Bob is your uncle',
                            isTrue: false,
                        },
                        {
                            answer: 'I don\'t know',
                            isTrue: false,
                        }
                    ]
                },
                {
                    id: 4,
                    type: 'quiz',
                    question: 'What is a storm in a teacup means?',
                    answers: [
                        {
                            answer: 'There is a storm in your tea',
                            isTrue: false,
                        },
                        {
                            answer: 'anger, worry about something unimportant',
                            isTrue: true,
                        },
                        {
                            answer: 'I don\'t know',
                            isTrue: false,
                        }
                    ]
                }
            ],
        }
    }
}
</script>