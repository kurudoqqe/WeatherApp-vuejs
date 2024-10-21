<script setup>
  import WeatherContent from "@/components/WeatherContent.vue";
  import axios from "axios";
  import {onMounted, ref, watch} from "vue";
  import LoadingSpinner from "@/components/LoadingSpinner.vue";

  const weatherData = ref([])
  const isLoading = ref(true);
  const city = ref(`London`)

  const getData = async () => {
    isLoading.value = true;
    try {
      const response = await axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${city.value}&units=metric&appid=${import.meta.env.VITE_API_KEY}`);
      weatherData.value = response.data;
      isLoading.value = false;
    } catch (error) {
      console.error('Произошла ошибка при получении данных:', error);
      setTimeout(() => {
        city.value = "London"
        getData();
      }, 7000)
    }
  }

  onMounted(async () => {
    await getData()
  });

  watch(city, () => {
    getData()
  })

</script>

<template>
  <main>
    <div class="section_blurred_img" :id="(typeof weatherData.main !== 'undefined' && weatherData.main.temp > 16) ? 'warm' : 'cold'">
      <div class="section_blurred_img-container">
        <div class="section_blurred_img-inner" :id="(typeof weatherData.main !== 'undefined' && weatherData.main.temp > 16) ? 'warm-main' : 'cold-main'">
          <WeatherContent :data="weatherData" :city="city" @update:city="city = $event" v-if="!isLoading" @click="a"/>
          <LoadingSpinner v-else/>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.section_blurred_img {
  background-size: contain;
  box-shadow: inset 0 0 50px #000;
  transition: 0.4s;

  .section_blurred_img-container {
    display: flex;
    justify-content: center;
    width: 100%;
    min-height: 100vh;
    backdrop-filter: blur(25px);
    background-image: linear-gradient(to bottom, rgba(0,0,0,0.25), rgba(0,0,0,0.75));

    .section_blurred_img-inner {
      background-image: url("../assets/images/warm-bg.jpg");
      background-size: cover;
      width: 360px;
      transition: 0.4s;
    }
  }
}

#warm {
  background-image: url("../assets/images/warm-bg.jpg");
}

#cold {
  background-image: url("../assets/images/cold-bg.jpg");
}

#warm-main {
  background-image: url("../assets/images/warm-bg.jpg");
}

#cold-main {
  background-image: url("../assets/images/cold-bg.jpg");
}
</style>