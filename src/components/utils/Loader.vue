<template>
  <section>
    <div class="loader">
      <span style="--i:1;"></span>
      <span style="--i:2;"></span>
      <span style="--i:3;"></span>
      <span style="--i:4;"></span>
      <span style="--i:5;"></span>
      <span style="--i:6;"></span>
      <span style="--i:7;"></span>
      <span style="--i:8;"></span>
      <span style="--i:9;"></span>
      <span style="--i:10;"></span>
      <span style="--i:11;"></span>
      <span style="--i:12;"></span>
      <span style="--i:13;"></span>
      <span style="--i:14;"></span>
      <span style="--i:15;"></span>
      <span style="--i:16;"></span>
      <span style="--i:17;"></span>
      <span style="--i:18;"></span>
      <span style="--i:19;"></span>
      <span style="--i:20;"></span>
    </div>
  </section>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';

@Options({
  name: 'Loader',
})
export default class HelloWorld extends Vue {}
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

section {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 30vh;
  background: transparent;
  animation: animateBg 5s linear infinite;
}

@keyframes animateBg {
  0% {
    filter: drop-shadow(0 0 0.5px #06ba87);
  }
  100% {
    filter: drop-shadow(0 0 1px #06f0ad);
  }
}

section .loader {
  position: relative;
  width: 70px;
  height: 70px;
}

section .loader span {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  transform: rotate(calc(18deg * var(--i)));
}

section .loader span::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #047857;
  box-shadow: 0 0 10px #cccccc;
  animation: animate 0.5s linear infinite;
  animation-delay: calc(0.05s * var(--i));
}

@keyframes animate {
  0% {
    transform: scale(1);
  }
  80%,100% {
    transform: scale(0);
  }
}
</style>
