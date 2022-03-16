<template>
  <div>
    <ul>
      <li>
        <button @click="loadGames" type="button" class="btn btn-primary">
          Primary
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
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
            console.log(this.gamesData.title)
          }

        });
    },
  },
};
</script>
