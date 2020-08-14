<template>
  <div id="app">
    <NavBar />
    <SelectItems 
      :countries = "countries"
    />
  </div>
</template>

<script>
import SelectItems from './components/SelectItems.vue'
import NavBar from './components/NavBar.vue'

export default {
  name: 'App',
  components: {
    SelectItems,
    NavBar
  },

  data() {
    return {
      countries: [],
    }
  },

  mounted: function() {
    fetch('https://raw.githubusercontent.com/dr5hn/countries-states-cities-database/master/countries%2Bstates%2Bcities.json', {
      method: 'get'
    })
    .then(response => {
      return response.json()
    })
    .then(jsonData => {
      this.countries = jsonData
    })
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
