<template>
    <h2 class="text-white text-center mt-3">15 funny idioms</h2>
    <CourseCarousel :materials="materials" />
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
            materials: sourceData.course,
        }
    }
}
</script>