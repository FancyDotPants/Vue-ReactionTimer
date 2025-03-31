<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    Click Me
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTimer: 0,
        };
    },
    mounted() {
        console.log("Component Mounted!");
        setTimeout(() => {
            this.showBlock = true;
            this.startTimer();
            //console.log(this.delay);
        }, this.delay)
        // runs when the component mounts.
    },
    updated() {
        //console.log("Component Updated!")
        //runs when the component updates.
    },
    unmounted() {
        //console.log("Component Unmounted!")
        // runs when the component unmounts or dismantled.
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTimer += 10;
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer);
            console.log("You reacted within " + this.reactionTimer + "ms");
            this.$emit('end', this.reactionTimer);
        },
    }
}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
        }
</style>