<script setup>
</script>

<template>

  <div class="bubbles">
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
  </div>

</template>

<style scoped>


.bubbles div {
  background: rgba(228, 174, 40, 0.375);
  border-radius: 100%;
  position: absolute;
  bottom: 0;
  animation: animatebubbles 4s linear infinite;
  z-index: 1;
}

.bubbles div:nth-child(1) {
  width: 4rem;
  height: 3.8rem;
  left: 4%;
  animation-duration: 4s;
}

.bubbles div:nth-child(2) {
  width: 3.2rem;
  height: 3rem;
  left: 25%;
  animation-duration: 5s;
}

.bubbles div:nth-child(3) {
  width: 2.8rem;
  height: 2.6rem;
  left: 40%;
  animation-duration: 5.2s;
}

.bubbles div:nth-child(4) {
  width: 1.3rem;
  height: 1.5rem;
  left: 50%;
  animation-duration: 7s;
}

.bubbles div:nth-child(5) {
  width: 3rem;
  height: 2.8rem;
  left: 65%;
  animation-duration: 3s;
}

.bubbles div:nth-child(6) {
  width: 4rem;
  height: 3.9rem;
  left: 80%;
  animation-duration: 4s;
}

@keyframes animatebubbles {
  0% {
    width: 0;
    height: 0;
  }
  3% {
    width: 1.7rem;
    height: 1.5rem;
  }
  50% {
    margin-left: 1rem;
    opacity: 0.5;
  }
  100% {
    transform: rotate(90deg);
    bottom: 100vh;
    background: rgba(255, 208, 88, 0.145);
  }
}
  
</style>