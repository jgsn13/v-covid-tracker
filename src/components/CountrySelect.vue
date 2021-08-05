<template>
  <select @change="onChange()"
  v-model="selected"
  class="block w-full p-3 mt-10 border rounded outline-none form-select">
    <option value="0">Select Country</option>
    <option v-for="country in countries" :value="country.ID" :key="country.ID">
      {{ country.Country }}
    </option>
  </select>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';

@Options({
  name: 'CountrySelect',
  props: {
    countries: Object,
  },
  methods: {
    onChange(): void {
      const country = this.countries.find((item: any) => item.ID === this.selected);

      this.$emit('get-country', country);
    },
  },
})
export default class CountrySelect extends Vue {
  selected = 0;
}
</script>
