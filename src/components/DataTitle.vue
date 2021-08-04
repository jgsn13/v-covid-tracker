<template>
  <div class="text-center">
    <h2 class="text-3xl font-bold">{{ text }}</h2>
    <div class="mt-4 mb-10 text-2xl">
      {{ timestamp }}
    </div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import moment from 'moment';

@Options({
  name: 'DataTitle',
  props: {
    text: String,
    dataDate: String,
  },
  computed: {
    timestamp(): string {
      return moment(this.dataDate).format('MMMM Do YYYY, h:mm:ss a');
    },
  },
})

export default class DataTitle extends Vue {}
</script>
