<template>
  <main v-if="!loading" class="home">
    <DataTitle :text="title" :dataDate="dataDate" />

    <DataBoxes :stats="stats" />

    <CountrySelect @get-country="getCountryData" :countries="countries" />

    <button v-if="stats.Country"
    @click="clearCountryData"
    class="p-3 mt-10 text-white bg-blue-700 rounded focus:outline-none hover:bg-blue-500">
      Clear Country
    </button>
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
import CountrySelect from '@/components/CountrySelect.vue';

@Options({
  name: 'Home',
  components: {
    Loader,
    DataTitle,
    DataBoxes,
    CountrySelect,
  },
  methods: {
    async fetchCovidData(): Promise<any> {
      const res = await fetch('https://api.covid19api.com/summary');
      const data = await res.json();
      return data;
    },
    getCountryData(country: any): void {
      this.stats = country;
      this.title = country.Country;
    },
    async clearCountryData() {
      this.loading = true;
      const data = await this.fetchCovidData();
      this.title = 'Global';
      this.stats = data.Global;
      /* this.loading = false; */
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
