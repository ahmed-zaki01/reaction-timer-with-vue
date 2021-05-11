<template>
  <p>Reaction Time - {{ score }} ms</p>
  <p v-if="rank" id="rank" :class="classObject">{{ rank }}</p>
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
    if (this.score < 250) {
      this.rank = "Ninja Fingers";
    } else if (this.score < 400) {
      this.rank = "Rapid Reflexes";
    } else {
      this.rank = "Snail pace...";
    }
  },

  computed: {
    classObject() {
      return {
        ninja: this.score < 250,
        rapid: this.score >= 250 && this.score < 400,
        snail: this.score >= 400,
      };
    },
  },
};
</script>

<style>
p#rank {
  font-size: 1.4em;
  font-weight: bold;
}

p.ninja {
  color: #0faf87;
}
p.rapid {
  color: turquoise;
}
p.snail {
  color: orangered;
}
</style>
