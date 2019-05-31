<template>
  <div class="home">
    <img :src="logo" class="Logo"/>
    <HomeSubject />
    
  </div>
</template>

<script>
// @ is an alias to /src
import HomeSubject from "@/components/HomeSubject.vue"
import logo from "../../static/logo/Logo-PSU.png"

export default {
  name: "home",
  components: {
    HomeSubject,
  },
  data: function(){
    return {
      image: logo
    }
  }
};
</script>
<style scoped>
</style>

