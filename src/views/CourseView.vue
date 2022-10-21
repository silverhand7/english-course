<template>
    <br>
    <h2 class="text-white text-center">15 funny idioms</h2>
    <div class="course">
        <CourseCarousel :materials="materials" />
    </div>
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

<style>
.course {
    margin:auto;
    max-width: 500px;
}
</style>