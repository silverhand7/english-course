<template>
    <div>
        <div class="flip-card" :class="{ clicked: isFlipped }">
            <div class="flip-card-inner">
                <div class="flip-card-front">
                    <span class="flip-number">{{ number }}</span>
                    <p>{{ name }}</p>
                </div>
                <div class="flip-card-back bg-primary text-light">
                    <div>
                        <p>{{ meaning }}</p>
                        <div class="line"></div>
                        <p><i>"{{ example }}"</i></p>
                    </div>
                </div>
                <div class="flip-card-button">
                    <div @click="flip">
                        <img src="../assets/images/flip-icon.jpg" alt="">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        number: {
            required: false,
            type: Number,
            default: 0,
        },
        name: {
            required: true,
            type: String,
        },
        meaning: {
            required: true,
            type: String,
        },
        example: {
            required: false,
            default: '',
            type: String,
        }
    },
    data() {
        return {
            isFlipped: false
        }
    },
    methods: {
        flip() {
            this.isFlipped = !this.isFlipped;
        }
    }
}
</script>

<style>
    .flip-card {
        background-color: transparent;
        width: 300px;
        height: 500px;
        perspective: 1000px;
        border-radius: 15px;
    }

    .flip-card-inner {
        position: relative;
        width: 100%;
        height: 100%;
        text-align: center;
        transition: transform 0.6s;
        transform-style: preserve-3d;
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        border-radius: 15px;
    }

    .flip-card.clicked .flip-card-inner {
        transform: rotateY(180deg);
    }

    .flip-card-front, .flip-card-back {
        position: absolute;
        width: 100%;
        height: 100%;
        -webkit-backface-visibility: hidden;
        backface-visibility: hidden;
        border-radius: 15px;
    }

    .flip-card-front {
        color: black;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 19px;
        line-height: 1.4em;
        padding: 15px;
        background: white;
    }

    .flip-number {
        position: absolute;
        top: 12px;
        left: 10px;
        padding: 10px 21px;
        border-radius: 12px;
        font-size: 26px;
    }

    .flip-card-back {
        z-index: -1;
        background-color: #2e5d2d;
        color: #fff;
        transform: rotateY(180deg);
        padding:15px;
        display: flex;
        align-items: center;
        justify-content: center;
        line-height: 1.4em;
    }

    .flip-card-button {
        z-index: 2;
        cursor: pointer;
        position: absolute;
        bottom: -25px;
        left: 50%;
        transform: translateX(-50%);
    }

    .flip-card-button div img {
        width: 50px;
        border-radius: 10px;
    }

    .line {
        border: 0.5px solid #ccc;
        margin:25px 0;
    }
</style>