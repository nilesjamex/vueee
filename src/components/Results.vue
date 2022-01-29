<template>
  <p>Reaction Time = {{ score }} ms </p>
  <p class="rank"> {{ rank }} </p>
</template>

<script>
export default {
    props: [ 'score' ],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 250) {
            this.rank = 'reflex guru!!!'
        } else if (this.score < 400) {
            this.rank = 'well, you tried but you can do better!!'
        } else {
            this.rank = 'snail pace blud, fix up!'
        }
    }
}
</script>

<style scoped>
.rank {
    font-size: 1.6rem;
    color: #333333;
    font-weight: bold;
}
</style>