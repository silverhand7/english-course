<template>
    <div class="question-card">
        <div>
            <p>{{ question }}</p>
            <ul class="answer-options">
                <li v-for="option in answers"
                    @click="clickAnswer(option)"
                    :class="[(isAnswered ?
                        (isCorrect && optionAnswer === option.answer) ? 'green' : '' : ''),
                        (isCorrection === option.answer ? 'green' : ''),
                        (isAnswered ? !isCorrect && optionAnswer === option.answer ? 'red' : '' : ''
                    )]"
                >{{ option.answer }}</li>
            </ul>
        </div>
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
            isCorrection: false,
        }
    },
    methods: {
        clickAnswer(answer) {
            if (!this.isAnswered) {
                this.optionAnswer = answer.answer;
                this.isAnswered = true;
                this.isCorrect = answer.isTrue;
                this.$emit('clickedAnswer', {
                    'isCorrect': this.isCorrect,
                });
                if (!this.isCorrect) {
                    const correctAnswer = this.answers.find(answer => answer.isTrue == true).answer;
                    this.isCorrection = correctAnswer;
                }
            }
        }
    }
}
</script>

<style>
    .question-card {
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        width: 300px;
        height: 500px;
        perspective: 1000px;
        text-align: left;
        padding:20px;
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 15px;
        background:white;
    }
    .answer-options {
        margin-left: 0;
        padding-left: 0;
        list-style: none;
    }

    .answer-options li {
        padding: 10px;
        border: 1px solid #ccc;
        margin-bottom:10px;
        cursor: pointer;
    }


    .green {
        background: #198754;
        color: white;
    }
    .red {
        background: #ff7373;
        color: white;
        animation: horizontal-shaking 0.25s;
    }

    @keyframes horizontal-shaking {
        0% { transform: translateX(0) }
        25% { transform: translateX(5px) }
        50% { transform: translateX(-5px) }
        75% { transform: translateX(5px) }
        100% { transform: translateX(0) }
    }
</style>