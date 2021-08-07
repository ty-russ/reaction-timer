<template>
  <p>your reaction time is {{ score }} milliseconds!</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  name: "Results",
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Awesome!!";
    } else if (this.score < 500) {
      this.rank = "Good!..you can do better";
    } else {
      this.rank = "meeeeh!...too slow";
    }
  },
};
</script>

<style scoped>
.rank {
  font: size 1.4em;
  color: green;
  font-weight: bold;
}
</style>
