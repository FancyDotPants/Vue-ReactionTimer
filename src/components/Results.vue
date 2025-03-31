<template>
  <p>Reaction Time: {{ score }}ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null,
        }
    },
    mounted() {
        if(this.score < 150){
            this.rank = "PERFECTTTT!!";
        } else if(this.score < 300) {
            this.rank = "Great effort. Try again?";
        } else if(this.score < 400) {
            this.rank = "That was okay.";
        } else {
            this.rank = "Are you blind or something? Keep practicing...";
        };
    }
}
</script>

<style>
    .rank {
        font-size: 1.4em;
        color: #0faf78;
        font-weight: bold;
    }
</style>