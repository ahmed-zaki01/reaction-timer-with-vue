<template>
  <div id="block" v-if="showBlock" @click="stopTimer">Click Me</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },

  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      console.log(this.reactionTime);
    },
  },
};
</script>

<style >
div#block {
  width: 400px;
  background: #0faf87;
  padding: 100px 0;
  margin: 40px auto;
  cursor: pointer;
  color: #e6e6e6;
  border-radius: 20px;
}
</style>
