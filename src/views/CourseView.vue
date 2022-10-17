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
                    name: 'A storm in a teacup',
                    meaning: 'a lot of unnecessary anger and worry about a matter that is not important',
                    example: 'She’s made an official complaint to the CEO about the type of cheese in the cheese sandwiches at the canteen. This seems to me to be a storm in a teacup.'
                },
                {
                    id: 2,
                    name: 'Bob’s your uncle!',
                    meaning: '"and there it is" or "and there you have it"',
                    example: 'To make a cup of mint tea; boil a kettle, add a tea bag, wait 2 minutes and Bob\'s your uncle!'
                },
            ]
        }
    }
}
</script>