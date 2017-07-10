<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input type="text" placeholder=" Enter your location" >
    <button v-on:click="getLocation" >Get Your Location</button>
      </div>
</template>
  


<script>

import axios from 'axios'
import API_KEY from '../constants'

export default {
  name: 'Weather',
  data () {
    return {
      msg: 'Weather Forecast',
      loc: ''
    }
  },
  methods: {
    getLocation : function(){
      axios.post(`https://www.googleapis.com/geolocation/v1/geolocate?key=AIzaSyBmcGc-h0bg0sT3DC-FWiStVmug3cRDobc`)
            .then(res => {
             this.loc = res.data.location
            })
            .catch(err => console.log(err))

    }
    
  }
}
</script>

<style scoped>
h1, h2 {
  font-weight: normal;
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
</style>
