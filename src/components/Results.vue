<template>
  <h1 class="mt-2">Reaction time:{{ score }} milliseconds!</h1>
  <p class="font-bold text-green-500 text-lg">Your rank is: {{rank}}!</p>
</template>
<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score <= 250) {
      this.rank = "God. Learn me jedi, please";
    } else if (this.score <= 400) {
      this.rank = "Normal. Not bad";
    } else {
      this.rank = "Looser... Go next one";
    }
  },
};
</script>
