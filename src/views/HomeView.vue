<template>
    <main v-if="!loading">
       this is the data
    </main>
    <main v-else class="flex flex-col align-center justify-center text-center " >
      <div class="text-gray-500 text-3xl mt-10 mb-6">
        Fetching Data
      </div>
      <img :src="loadingImage" class="w-24 m-auto" alt="img">
    </main>
</template>

<script>
  export default {
    components:{},
    data() {
      return {
        loading:true,
        title:'Global',
        dataDate:"",
        stats:{},
        countries:[],
        loadingImage:require('../assets/icons8-hourglass.gif')

      }
    },
    methods:{
      async fetchCovidData(){
        const response = await fetch('https://api.covid19api.com/summary')
        const data = await response.json()
       
        return data
      }
    },
    async created(){
      const data  = await this.fetchCovidData() 
      this.dataDate = data.Date
      this.stats = data.Global
      this.countries = data.Countries
      this.loading = false
    }
  }
</script>

<style scoped>

</style>
