<template>
  <select
    @change="onChange()"
    v-model="select"
    class="form-select mt-10 block w-full border p-3 rounded"
  >
    <option value="0">Select Country</option>
    <option
      v-for="(country, index) in countries"
      :key="index"
      :value="country.ID"
    >
      {{ country.Country }}
    </option>
  </select>
</template>

<script>
export default {
  props: ["countries"],
  data() {
    return {
      select: 0,
    };
  },
  methods: {
    onChange(){
        const country =  this.countries.find((item) => item.ID === this.select)
        console.log(country)
        this.$emit('get-country', country)
    }
  },
};
</script>

<style scoped></style>
