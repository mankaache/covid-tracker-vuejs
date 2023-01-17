<template>
  <header-file></header-file>
  <div class="container">
    <router-view/>
  </div>
  
</template>

<script>
import HeaderFile from "@/components/HeaderFile.vue"
export default {
  components:{
    HeaderFile
  } 
}
</script>