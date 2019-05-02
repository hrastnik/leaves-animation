<template>
  <div class="leaves__container">
    <img class="leaves__image" src="@/assets/leaf.png" alt="leaf" />
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.leaves {
  &__container {
    position: relative;
  }

  &__image {
    position: absolute;

    left: 50vw;

    min-width: 50px;
    width: 16vw;
    max-width: 300px;
    animation: falling 8s linear 0s infinite;
  }
}

@keyframes falling {
  from {
    transform: translateY(-100%);
  }
  to {
    transform: translateY(calc(100vh + 100%));
  }
}
</style>

