<template>
  <main v-if="!loading">
    <data-title :text="title" :dataDate="dataDate"></data-title>
    <data-boxes :stats="stats"></data-boxes>
    <country-select :countries="countries"></country-select>
  </main>
  <main v-else class="flex flex-col align-center justify-center text-center">
    <div class="text-gray-500 text-3xl mt-10 mb-6">Fetching Data</div>
    <img :src="loadingImage" class="w-24 m-auto" alt="img" />
  </main>
</template>

<script>
import DataTitle from "@/components/DataTitle.vue";
import DataBoxes from "@/components/DataBoxes.vue";
import CountrySelect from "@/components/CountrySelect.vue";
export default {
  components: {
    DataTitle,
    DataBoxes,
    CountrySelect,
  },
  data() {
    return {
      loading: true,
      title: "Global",
      dataDate: "",
      stats: {},
      countries: [],
      loadingImage: require("../assets/icons8-hourglass.gif"),
    };
  },
  methods: {
    async fetchCovidData() {
      const response = await fetch("https://api.covid19api.com/summary");
      const data = await response.json();
      console.log(data);
      return data;
    },
  },
  async created() {
    const data = await this.fetchCovidData();
    console.log(data);
    this.dataDate = data.Date;
    this.stats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  },
};
</script>

<style scoped></style>
