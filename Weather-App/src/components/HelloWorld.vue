<template>
  <div class="weather-card">
    <h1>Weather App</h1>
    <div class="search-bar">
      <input type="text" v-model="city" placeholder="Enter a city"><br><br>
      <button @click="getWeather">Get Weather</button>
    </div>
    <div v-if="weather" class="weather-info">
      <h2>{{ weather.name }}</h2>
      <div class="weather-details">
        <div class="weather-icon">
          <img :src="`http://openweathermap.org/img/wn/${weather.weather[0].icon}.png`" alt="Weather Icon">
          <p>{{ weather.weather[0].description }}</p>
        </div>
        <div class="weather-temperature">
          <p class="temperature">{{ weather.main.temp }}°C</p>
          <p>Feels like: {{ weather.main.feels_like }}°C</p>
          <p>Humidity: {{ weather.main.humidity }}%</p>
          <p>Wind Speed: {{ weather.wind.speed }} m/s</p>
          <p>Visibility: {{ (weather.visibility / 1000).toFixed(2) }} km</p>
          <p>Sunrise: {{ formatTime(weather.sys.sunrise) }}</p>
          <p>Sunset: {{ formatTime(weather.sys.sunset) }}</p>
        </div>
      </div>
    </div>
    <div v-if="error" class="error-message">
      <p>{{ error }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      city: '',
      weather: null,
      error: null
    };
  },
  methods: {
    getWeather() {
      fetch(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=cbc42ca72b55a7ab341f9b53e0e7361c
      `)
        .then(response => {
          if (!response.ok) {
            throw new Error('City not found!');
          }
          return response.json();
        })
        .then(data => {
          this.weather = data;
          this.error = null;
        })
        .catch(error => {
          console.error('Error fetching weather:', error);
          this.error = 'Error fetching weather. Please try again.';
          this.weather = null;
        });
    },
    formatTime(timestamp) {
      const date = new Date(timestamp * 1000);
      return `${date.getHours()}:${('0' + date.getMinutes()).slice(-2)}`;
    }
  }
}
</script>

<style>
.weather-card {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  border-radius: 15px;
  background: linear-gradient(to right, #79CBCA, #77A1D3);
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
}

.weather-card h1 {
  text-align: center;
  color: #fff;
  margin-bottom: 20px;
}

.search-bar {
  margin-bottom: 20px;
}

.search-bar input[type="text"] {
  width: 70%;
  padding: 10px;
  border: none;
  border-radius: 5px 0 0 5px;
}

.search-bar button {
  width: 30%;
  padding: 10px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 0 5px 5px 0;
  cursor: pointer;
}

.search-bar button:hover {
  background-color: #0056b3;
}

.weather-info {
  text-align: center;
  color: #fff;
}

.weather-details {
  display: flex;
  justify-content: center;
  align-items: center;
}

.weather-icon img {
  width: 100px;
}

.weather-temperature {
  text-align: left;
}

.temperature {
  font-size: 24px;
  font-weight: bold;
}

.error-message {
  color: red;
  margin-top: 20px;
}
</style>
