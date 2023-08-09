<template>
  <div
    v-if="showBlock"
    @click="stopTimer"
    class="bg-green-500 cursor-pointer max-w-max p-24 mt-6 mx-auto rounded-md text-2xl"
  >
    Click me!
  </div>
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
      this.showBlock = !this.showBlock;
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
      this.showBlock = !this.showBlock;
      this.$emit('end',this.reactionTime)
    },
  },
};
</script>
