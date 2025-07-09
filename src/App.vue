<template>
  <div className="wrapper">
    <h1>Weather App</h1>
    <p>Check the weather in {{ city == '' ? 'your city' : city }}</p>
    <input type="text" placeholder="Enter your city" v-model="city">
    <button v-show="city != ''" @click="getWeather()">go</button>
    <p className="error">{{ error }}</p>

    <div v-show="info != null">
      <p>{{ curWeather }}</p>
      <p>{{ curTemp }}</p>
      <p>{{ feelsLike }}</p>
      <p>{{ minTemp }}</p>
      <p>{{ maxTemp }}</p>
      <p>{{ humidity }}</p>
      <p>{{ windSpeed }}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      city: '',
      error: '',
      info: null,
    }
  },
  methods: {
    getWeather() {
      if (this.city.trim().length < 2) {
        this.error = 'Need more than 1 symbol'
        return false
      }
      this.error = ''

      axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&APPID=d3de50686c876ef67661ed5a7ae801d0`)
      .then(response => this.info = response.data)
    },
  },
  computed: {
    curWeather() {
      return this.info ? 'Current weather is ' + this.info.weather[0].description : ''
    },
    curTemp() {
      return this.info ? 'Current temperature is ' + this.info.main.temp : ''
    },
    feelsLike() {
      return this.info ? 'Feels like ' + this.info.main.feels_like : ''
    },
    minTemp() {
      return this.info ? 'Minimal temperature is ' + this.info.main.temp_min : ''
    },
    maxTemp() {
      return this.info ? 'Maximal temperature is ' + this.info.main.temp_max : ''
    },
    humidity() {
      return this.info ? 'Current humidity is ' + this.info.main.humidity : ''
    },
    windSpeed() {
      return this.info ? 'Current wind speed is ' + this.info.wind.speed : ''
    },
  },
}
</script>

<style scoped>
.wrapper {
  width: 900px;
  height: 500px;
  border-radius: 50px;
  background: rgba(93, 83, 237, 1);
  padding: 20px;
  text-align: center;
  color: #fff;
}

.wrapper h1 {
  margin-top: 50px;
}

.wrapper p {
  margin-top: 20px;
}

.wrapper input {
  margin-top: 30px;
  background: transparent;
  border: 0;
  outline: none;
  color: #fff;
  font-size: 14px;
  padding: 5px 8px;
}

.wrapper input::placeholder {
  color: #fff;
  text-align: center;
}

.wrapper input:focus {
  border-bottom: 2px solid #67b7e6;
}

.wrapper button {
  color: #fff;
  background: #67b7e6;
  border-radius: 10px;
  border: none;
  padding: 10px 15px;
  margin-left: 20px;
  cursor: pointer;
  transition: transform 500ms ease;
}

.wrapper button:hover {
  transform: scale(1.1) translateY(-5px);
}

.error {
  color: tomato;
}

</style>
