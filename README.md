# WEATHER APP 
## Using HTML , CSS , Javascript 
## javascript 
``` javascript
// API CALL
const url = 'https://weather-by-api-ninjas.p.rapidapi.com/v1/weather?city=Seattle';
const options = {
	method: 'GET',
	headers: {
		'X-RapidAPI-Key': 'f6c0d1aa61mshf56ff03556b4190p10cc9ejsn3255ff92075b',
		'X-RapidAPI-Host': 'weather-by-api-ninjas.p.rapidapi.com'
	}
};
const getWeather = (city) => {
  const url =
  'https://weather-by-api-ninjas.p.rapidapi.com/v1/weather?city='+ city;

  cityName.innerHTML = city;

  fetch(url, options)
    .then((response) => response.json()) // Parse the response as JSON
    .then((response) => {
      console.log(response);
      cloud_pct.innerHTML = response.cloud_pct;
      temp.innerHTML = response.temp;
      temp2.innerHTML = response.temp;
      feels_like.innerHTML = response.feels_like;
      humidity.innerHTML = response.humidity;
      humidity2.innerHTML = response.humidity;
      min_temp.innerHTML = response.min_temp;
      max_temp.innerHTML = response.max_temp;
      wind_speed.innerHTML = response.wind_speed;
      wind_speed2.innerHTML = response.wind_speed;
      wind_degrees.innerHTML = response.wind_degrees;
      sunrise.innerHTML = response.sunrise;
      sunset.innerHTML = response.sunset;
    })
    .catch((err) => console.error(err));
};

const getWeatherAll = () => {
  const cities = ["delhi", "bengaluru", "lucknow", "bhopal", "surat"];
  cities.map(async (city) => {
    const url =
      "https://weather-by-api-ninjas.p.rapidapi.com/v1/weather?city=" + city;

    await fetch(url, options)
      .then((res) => res.json()) // Parse the response as JSON
      .then((response) => {
        const row = document.getElementById(city);
        row.querySelector(".cloud_pct").innerHTML = response.cloud_pct;
        row.querySelector(".temp").innerHTML = response.temp;
        row.querySelector(".feels_like").innerHTML = response.feels_like;
        row.querySelector(".humidity").innerHTML = response.humidity;
        row.querySelector(".min_temp").innerHTML = response.min_temp;
        row.querySelector(".max_temp").innerHTML = response.max_temp;
        row.querySelector(".wind_speed").innerHTML = response.wind_speed;
        row.querySelector(".wind_degrees").innerHTML = response.wind_degrees;
        row.querySelector(".sunrise").innerHTML = response.sunrise;
        row.querySelector(".sunset").innerHTML = response.sunset;
      })
      .catch((err) => console.error(err));
  });
};

submit.addEventListener("click", (e) => {
  e.preventDefault(); // Fix the typo here
  getWeather(city.value);
});

// You might want to replace "Delhi" with the default city value if needed
getWeather("Haridwar");
getWeatherAll();




  window.onload = function() {
    updateDateTime();
    setInterval(updateDateTime, 1000); // Update every second
};

function updateDateTime() {
    const now = new Date();
    
    const dateElement = document.getElementById('date');
    dateElement.textContent = `Date: ${now.toLocaleDateString()}`;
    
    const timeElement = document.getElementById('time');
    timeElement.textContent = `Time: ${now.toLocaleTimeString()}`;
    
    const dayElement = document.getElementById('day');
    const daysOfWeek = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'];
    dayElement.textContent = `Day: ${daysOfWeek[now.getDay()]}`;
    
    const monthElement = document.getElementById('month');
    const months = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'];
    monthElement.textContent = `Month: ${months[now.getMonth()]}`;
}


```