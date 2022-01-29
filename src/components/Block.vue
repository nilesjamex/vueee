<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      CLICK ME!
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTimer: 0
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTimer += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit('end', this.reactionTimer)
        }
    }
}
</script>

<style scoped>
.block {
    width: 75%;
    height: 200px;
    border-radius: 20px;
    background: #333333;
    color: #f2f2f3;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>