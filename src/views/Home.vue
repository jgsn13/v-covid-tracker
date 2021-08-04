<template>
  <main v-if="!loading" class="home">
    <DataTitle :text="title" :dataDate="dataDate" />

    <DataBoxes :stats="stats" />
  </main>

  <main class="flex flex-col justify-center text-center align-middle" v-else>
    <div class="mt-10 mb-6 text-3xl text-gray-500">
      Fetching Data
    </div>
    <Loader />
  </main>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';

import Loader from '@/components/utils/Loader.vue';
import DataTitle from '@/components/DataTitle.vue';
import DataBoxes from '@/components/DataBoxes.vue';

@Options({
  name: 'Home',
  components: {
    Loader,
    DataTitle,
    DataBoxes,
  },
  methods: {
    async fetchCovidData(): Promise<any> {
      const res = await fetch('https://api.covid19api.com/summary');
      const data = await res.json();
      return data;
    },
  },
  async created() {
    const data = await this.fetchCovidData();

    this.dataDate = data.Date;
    this.stats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  },
})
export default class Home extends Vue {
  loading = true;

  title = 'Global';

  dataDate = '';

  stats = {};

  countries: string[] = [];
}
</script>
