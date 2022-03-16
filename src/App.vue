<template>
    <the-header-vue></the-header-vue>
    <The-games-vue></The-games-vue>
</template>

<script>
import TheHeaderVue from "./components/TheHeader.vue"
import TheGamesVue from "./components/TheGames.vue"
export default {
    components: {TheHeaderVue, TheGamesVue },
   
}
</script>