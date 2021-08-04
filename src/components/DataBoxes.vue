<template>
  <div class="grid md:grid-cols-2 gap-4">
    <!-- Box 1 -->
    <div class="p-10 text-center bg-green-100 shadow-md">
      <h3 class="mb-4 text-3xl font-bold text-green-900">Cases</h3>

      <div class="mb-4 text-2xl">
        <span class="font-bold">New:</span>
        {{ numberWithCommas(stats.NewConfirmed) }}
      </div>
      <div class="mb-4 text-2xl">
        <span class="font-bold">Total:</span>
        {{ numberWithCommas(stats.TotalConfirmed) }}
      </div>
    </div>

    <!-- Box 2 -->
    <div class="p-10 text-center bg-green-200 shadow-md">
      <h3 class="mb-4 text-3xl font-bold text-green-900">Deaths</h3>

      <div class="mb-4 text-2xl">
        <span class="font-bold">New:</span>
        {{ numberWithCommas(stats.NewDeaths) }}
      </div>
      <div class="mb-4 text-2xl">
        <span class="font-bold">Total:</span>
        {{ numberWithCommas(stats.TotalDeaths) }}
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';

@Options({
  name: 'DataBoxes',
  props: {
    stats: Object,
  },
  methods: {
    numberWithCommas(n: number): string {
      return n.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
    },
  },
})
export default class DataBoxes extends Vue {}
</script>
