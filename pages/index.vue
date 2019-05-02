<template>
  <section class="container">
    <div
      class="container__background"
      :class="{ 'container__background--green': isGreen }"
    />
    <Leaves />
  </section>
</template>

<script>
import Leaves from "~/components/Leaves.vue";

export default {
  data() {
    return {
      isGreen: false
    };
  },
  components: {
    Leaves
  },
  mounted() {
    this.isGreen = true;
  }
};
</script>

<style scoped>
.container {
  min-height: 100vh;
  overflow: hidden;
  position: relative;
}

.container__background {
  transition: all 5s;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background: radial-gradient(#5b9e48, #174245);
  opacity: 0;
}

.container__background--green {
  opacity: 1;
}
</style>
