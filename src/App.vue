<template>
  <div id="app">
    <h1>MZ Euro Sweepstakes</h1>

    <div v-for="(value, key, index) in teams" v-bind:key="index">
      <FootballTeams :teamData="{value}" />
    </div>

  </div>
</template>

<script>
import FootballTeams from './components/FootballTeams.vue';
import TeamData from './src/data/data.json';
import UserData from './src/user.json';

export default {
  name: 'App',
  components: {
    FootballTeams
  },
  computed: {
    teams() {
      const newTeamData =  TeamData.standings.map((team) => {
        for(var i = 0; i < team.table.length; i++)
        {
          //console.log(team.table[i].team.id + " - " + team.table[i].team.name); // Reveal this to find out names and country
          const teamId = team.table[i].team.id;
          team.table[i].team.user = UserData.filter((userTeam) => userTeam.teamId == teamId).map((userTeam) => userTeam)[0]; // return just the user
        }
        return team;
      })
      return newTeamData;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
