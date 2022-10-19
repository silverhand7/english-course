<template>
    <CourseCarousel :slides="slides" />
</template>

<script>
import CourseCarousel from '@/components/CourseCarousel.vue';
import sourceData from '@/data.json';

export default {
    components: {
        CourseCarousel
    },
    data() {
        return {
            slides: sourceData.course,
        }
    }
}
</script>