<template>
  <div class="leaves__container">
    <div class="leaves__outer leaves__left-right">
      <div class="leaves__falling ">
        <img
          class="leaves__rotate leaves__image"
          src="@/assets/leaf.png"
          alt="leaf"
        />
      </div>
    </div>

    <div class="leaves__outer leaves__left-right">
      <div class="leaves__falling ">
        <img
          class="leaves__rotate leaves__image"
          src="@/assets/leaf.png"
          alt="leaf"
        />
      </div>
    </div>

    <div class="leaves__outer leaves__left-right">
      <div class="leaves__falling ">
        <img
          class="leaves__rotate leaves__image"
          src="@/assets/leaf.png"
          alt="leaf"
        />
      </div>
    </div>

    <div class="leaves__outer leaves__left-right">
      <div class="leaves__falling ">
        <img
          class="leaves__rotate leaves__image"
          src="@/assets/leaf.png"
          alt="leaf"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.leaves__container {
  position: relative;
  perspective: 600px;
}

.leaves__outer {
  position: absolute;

  &:nth-child(1) {
    left: 5vw;
  }
  &:nth-child(2) {
    left: 30vw;
  }
  &:nth-child(3) {
    left: 50vw;
  }
  &:nth-child(4) {
    left: 70vw;
  }
}

.leaves__left-right {
  animation: left-right 3s ease-in-out 0s infinite;
}

$widths: 17vw 20vw 14vw 21vw;
$mobile-widths: 40vw 50vw 35vw 45vw;

$delays: 0s -4s -2s -6s;
$sway-delays: -0.8s -0.15s -0.22s 0s;

@for $i from 1 through 4 {
  .leaves__outer:nth-child(#{$i}) {
    .leaves__image {
      min-width: 50px;
      width: nth($widths, $i);
      max-width: 350px;

      @media (max-width: 500px) {
        width: nth($mobile-widths, $i);
        max-width: 500px;
      }
    }
    .leaves__falling {
      animation: falling-#{$i} 8s linear nth($delays, $i) infinite;
    }

    .leaves__rotate {
      animation: sway 3s ease-in-out nth($sway-delays, $i) infinite;
    }
  }
}

@keyframes left-right {
  0% {
    transform: translateX(5vw);
  }
  50% {
    transform: translateX(-5vw);
  }
  100% {
    transform: translateX(5vw);
  }
}

$initX: 0px, 0px, 0px, 0px;
$destX: 10vw, 20vw, 15vw, 10vw;

$initZ: 0px, 0px, 0px, 0px;
$destZ: 300px, -200px, 400px, -250px;

$destR: 270deg -360deg -270deg 360deg;

@for $i from 1 through 4 {
  @keyframes falling-#{$i} {
    0% {
      opacity: 1;
      transform: translate3d(nth($initX, $i), -100%, nth($initZ, $i))
        rotateZ(0deg);
    }
    80% {
      opacity: 1;
    }
    100% {
      opacity: 0;
      transform: translate3d(
          nth($destX, $i),
          calc(100vh + 100%),
          nth($destZ, $i)
        )
        rotateZ(nth($destR, $i));
    }
  }
}
@keyframes sway {
  0% {
    transform: rotateX(25deg) rotateY(-25deg) rotateZ(-45deg);
  }
  50% {
    transform: rotateX(-25deg) rotateY(25deg) rotateZ(45deg);
  }
  100% {
    transform: rotateX(25deg) rotateY(-25deg) rotateZ(-45deg);
  }
}
</style>

