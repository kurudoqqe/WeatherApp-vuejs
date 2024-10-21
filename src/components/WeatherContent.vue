<script setup>
import {computed, onMounted, ref} from "vue";

  const props = defineProps({
    data: {
      type: Object,
      required: true
    },
    city: {
      type: String,
      required: true
    }
  })

  const emit = defineEmits(['update:city']);

  const weatherNow = ref('')
    const inputText = ref('')

    const getDate = computed(() => {
      let today = new Date();
      let dd = String(today.getDate()).padStart(2, '0');
      let mm = String(today.getMonth() + 1).padStart(2, '0'); //January is 0!
      let yyyy = today.getFullYear();
      today = dd + '/' + mm + '/' + yyyy;
      return today
    })

  const sendData = () => {
    emit('update:city', inputText.value); // Используем emit для передачи нового значения
  }

  onMounted(() => {
    const weatherList = Object.values(props.data.weather)
    weatherList.map(weather => {
      weatherNow.value = weather.main
    })
  })

</script>

<template>
  <div class="shadow-inner">
    <input type="text" placeholder="Search..." v-model="inputText" @keypress.enter="sendData" />
    <div class="weather-wrap">
      <div>{{data.name}}, {{data.sys.country}}</div>
      <div>{{ getDate }}</div>
    </div>
    <div class="weather-box">
      <div>{{data.main.temp.toFixed()}}°C</div>
      <div>{{ weatherNow }}</div>
    </div>
  </div>
</template>

<style scoped>
.shadow-inner {
  background-image: linear-gradient(to bottom, rgba(0,0,0,0.25), rgba(0,0,0,0.75));
  height: 100%;
}
.shadow-inner input {
  margin: 1.5rem 0 1.5rem 1rem;
  padding: 15px 35px;
  background-color: #eaeff4;
  color: #313131;
  font-size: 20px;
  appearance: none;
  border: none;
  outline: none;
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 0 16px 0 16px;
  transition: 0.4s;

  &:focus {
    box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
    background-color: rgba(255, 255, 255, 0.75);
    border-radius: 16px 0px 16px 0px;
  }
}
.weather-wrap {
  color: #FFF;
  text-align: center;
  div:first-child {
    font-size: 32px;
    font-weight: 500;
    text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
    margin-bottom: 0.25rem;
  }
  div:last-child {
    font-size: 20px;
    font-weight: 100;
    font-style: italic;
    font-family: 'Century Schoolbook', sans-serif;
  }
}

.weather-box {
  color: #FFF;
  div:first-child {
    padding: 10px 25px;
    font-size: 102px;
    font-weight: 900;
    text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
    background-color:rgba(255, 255, 255, 0.25);
    border-radius: 16px;
    margin: 1.75rem 1.75rem;
    min-width: 18rem;
    box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
    user-select: none;
  }

  div:last-child {
    color: #FFF;
    font-size: 48px;
    font-weight: 700;
    font-style: italic;
    text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
    margin-left: 6rem;
  }
}
</style>