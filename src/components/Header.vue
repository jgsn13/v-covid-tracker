<template>
  <header class="p-4 mb-10 text-center text-white bg-green-700">
    <div class="mb-3 text-3xl font-bold md:text-5xl">
      <FontAwesomeIcon :icon="['fas', 'viruses']" />
      Covid-19 Tracker
    </div>
    <p>API by <a class="text-green-200" href="https://covid19api.con" target="_blank">covid19api.com</a></p>
  </header>
</template>

<script lang="ts">
import { Vue } from 'vue-class-component';

import { library } from '@fortawesome/fontawesome-svg-core';
import { faViruses } from '@fortawesome/free-solid-svg-icons';

library.add(faViruses);

export default class HelloWorld extends Vue {}
</script>
