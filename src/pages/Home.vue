<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <HomeSubject />
  </div>
</template>

<script>
// @ is an alias to /src
import HomeSubject from "@/components/HomeSubject.vue";

export default {
  name: "home",
  components: {
    HomeSubject
  }
};
</script>
