<template>
  <nav class="navbar d-flex">
    <a class="navbar-brand" href="#"
      ><h3><i class="fas fa-futbol"></i>SoccerLeague</h3>
    </a>
    <div class="navbar-nav d-flex flex-row-reverse">
      <the-clock-vue class="nav-item"></the-clock-vue>
    </div>
  </nav>
</template>

<script>
import TheClockVue from "./TheClock.vue";

export default {
  components: {TheClockVue},
  data() {
    return {
      fullDate: "",
    };
  },
 
  
};
</script>
