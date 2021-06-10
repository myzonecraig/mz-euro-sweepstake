<template>
  <div class="teams-container">
    <h3>{{teamData.value.group | formatString}}</h3>
    
    <div class="teams-row">
        <div v-for="(value, key, index) in teamData.value.table" v-bind:key="index" class="teams-row-item">
        <img :src="value.team.crestUrl" width="85px" /><br />
        
        <h4>{{value.team.name}}</h4>
        <small>{{ value.team.user }}</small>
        </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'FootballTeams',
  props: {
    teamData: Object
  },
  filters: {
    formatString: function (value) {
        if (!value) return ''
        value = value.toString()
        return value.replace("_", " ");
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.teams-container {
    width: 960px;
    margin:0 auto;
}
.teams-row {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    flex-wrap: nowrap;
    padding:20px 0px;
}
.teams-row-item {
    width:25%;
}
.teams-row-item img {
    border-radius: 5px;
    box-shadow: rgba(0, 0, 0, 0.16) 0px 1px 4px;
}
</style>
