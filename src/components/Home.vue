<template>
  <div class="hello">
    <h1>Welcome</h1>
    <h3>{{msg}}</h3>
  </div>
</template>

<script>
import axios from 'axios'

const API_KEY = '1e53985cce01955957837a83c43ac02d'
const API_URL = 'http://api.openweathermap.org/data/2.5/weather'
let city = 'London,uk'

export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Loading API'
    }
  },
  created () {
    this.fetchData()
  },
  methods: {
    fetchData () {
      axios({
        method: 'get',
        url: API_URL,
        params: {
          appid: API_KEY,
          q: city
        }
      }).then((response) => {
        console.log(response)
        let weather = response.data.weather[0].main
        let description = response.data.weather[0].description
        let city = response.data.name

        this.msg = `${city} weather: ${weather} (${description})`
      }).catch(reason => {
        this.msg = 'Error getting API data'
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
</style>
