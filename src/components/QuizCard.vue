<template>
    <div>
        <p>{{ question }}</p>
        <ul>
            <li v-for="option in answers"
                @click="clickAnswer(option)"
                :class="[(isAnswered ? isCorrect && optionAnswer === option.answer ? 'green' : '' : ''), (isAnswered ? !isCorrect && optionAnswer === option.answer ? 'red' : '' : '')]"
            >{{ option.answer }}</li>
        </ul>
    </div>
</template>

<script>
export default {
    props: {
        question: {
            required: true,
            type: String
        },
        answers: {
            required: true,
            type: Array,
        }
    },
    data() {
        return {
            optionAnswer: '',
            isAnswered: false,
            isCorrect: false,
        }
    },
    methods: {
        clickAnswer(answer) {
            this.optionAnswer = answer.answer;
            this.isAnswered = true;
            this.isCorrect = answer.isTrue;
        }
    }
}
</script>