<template>
  <div class="home">
    <h1>Warzone Stats</h1>
    <b-container>
      <b-row>
        <b-col class="border border-dark"
          ><h3>Level : {{ wzstats.level }}</h3></b-col
        >

        <b-col class="border border-dark"
          ><h3>KD Ratio : {{ wzstats.lifetime.all.properties.kdRatio }}</h3></b-col
        >
      </b-row>
      <b-row>
        <b-col class="border border-dark"
          ><h3>levelXpRemainder : {{ wzstats.levelXpRemainder }}</h3></b-col
        >
        <b-col class="border border-dark"
          ><h3>levelXpGained : {{ wzstats.levelXpGained }}</h3></b-col
        >
      </b-row>
      <b-row>
        <b-col class="border border-dark"
          ><h3>kills : {{ wzstats.lifetime.all.properties.kills }}</h3></b-col
        >
        <b-col class="border border-dark">
          <h3>deaths : {{ wzstats.lifetime.all.properties.deaths }}</h3></b-col
        >
      </b-row>
      <b-row>
        <b-col class="border border-dark"
          ><h3>totalXp : {{ wzstats.totalXp }}</h3></b-col
        >
        <b-col class="border border-dark"
          ><h3>prestige : {{ wzstats.prestige }}</h3></b-col
        >
      </b-row>
      <b-row>
        <b-col class="border border-dark"
          ><h3>score : {{ wzstats.lifetime.all.properties.score }}</h3></b-col
        >
        <b-col class="border border-dark"
          ><h3>
            timePlayedTotal :
            {{ wzstats.lifetime.all.properties.timePlayedTotal }}
          </h3></b-col
        >
      </b-row>
      <b-row>
        <b-col class="border border-dark"
          ><h3>
            totalGamesPlayed :
            {{ wzstats.lifetime.all.properties.totalGamesPlayed }}
          </h3></b-col
        >
        <b-col class="border border-dark"
          ><h3>assists : {{ wzstats.lifetime.all.properties.assists }}</h3>
        </b-col>
      </b-row>
      <b-row>
        <b-col class="border border-dark"
          ><h3>
            suicides : {{ wzstats.lifetime.all.properties.suicides }}
          </h3></b-col
        >
        <b-col class="border border-dark"
          ><h3>
            timeProne : {{ wzstats.lifetime.accoladeData.properties.timeProne }}
          </h3></b-col
        >
      </b-row>
    </b-container>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";

const options = {
  method: "GET",
  url:
    "https://call-of-duty-modern-warfare.p.rapidapi.com/multiplayer/Granaino_BUAB/psn",
  headers: {
    "x-rapidapi-key": "6001a4e8b3mshe0baf1d16d76c04p1082d4jsn4c69a8766f93",
    "x-rapidapi-host": "call-of-duty-modern-warfare.p.rapidapi.com",
  },
};

export default {
  name: "Home",
  components: {},
  data() {
    return {
      wzstats: [],
    };
  },
  created() {
    this.getWzStats();
  },
  methods: {
    async getWzStats() {
      const response = await axios.request(options);
      this.wzstats = response.data;
      console.log(this.wzstats);
    },
  },
  computed: {
    average: function() {
      let averagekd = 0;
      return (averagekd =
        wzstats.lifetime.all.properties.kills /
        wzstats.lifetime.all.properties.death);
    },
  },
};
</script>
