<template>
  <div>
    <ul v-for="gameData in gamesData" :key="gameData.id">
        <the-base-card-vue @click="gameData.matchUrl">
            <h3> {{gameData.title}} </h3>
            <h2> {{gameData.league}} </h2>
            <p> {{gameData.thumbnail}} </p>
            <p> {{gameData.matchDate}} </p>
        </the-base-card-vue>
    </ul>
  </div>
</template>

<script>
import TheBaseCardVue from "./UI/TheBaseCard.vue";
export default {
    components: {TheBaseCardVue},
  data() {
      return {
          gamesData: []
      }
  },
  methods: {
    loadGames() {
      fetch(
        "https://www.scorebat.com/video-api/v3/feed/?token=MTU1NjhfMTY0NzMzMzczOF8wOTBjY2I4YjRlMDgzYmVmYWE2YjFlMzcwMTkyOTYxMjIwZGU5MjNl"
      )
        .then((res) => {
          if (res.ok) {
            return res.json();
          }
        })
        .then((data) => {
          const dataSetOne = data.response;
          const results = [];
          for (let i = 0; i < dataSetOne.length; i++) {
              results.push({ 
                  id: i,
                  title: dataSetOne[i].title,
                  matchUrl: dataSetOne[i].matchviewUrl,
                  league: dataSetOne[i].competition,
                  thumbnail: dataSetOne[i].thumbnail,
                  matchDate: dataSetOne[i].date
               })
              this.gamesData = results
            // console.log(dataSetOne[i].matchviewUrl);
        
          }

        });
    },
  },
  mounted(){
      this.loadGames();
  }
};
</script>
