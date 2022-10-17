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
                    name: 'Course 1',
                    description: 'Lorem'
                },
                {
                    id: 2,
                    name: 'Course 2',
                    description: 'Lorem Ipsum Course 2'
                },
            ]
        }
    }
}
</script>