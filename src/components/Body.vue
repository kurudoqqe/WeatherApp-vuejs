<script setup>

</script>

<template>
  <main>
    <div class="section_blurred_img">
      <div class="section_blurred_img-container">
        <div class="section_blurred_img-inner">
          <div class="shadow-inner">
            <input type="text" placeholder="Search...">
            <div class="weather-wrap">
              <div>Rostov-on-Don, Russia</div>
              <div>Monday 20 January 2020</div>
            </div>
            <div class="weather-box">
              <div>9°C</div>
              <div>Rain</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.section_blurred_img {
  background-image: url("../assets/images/cold-bg.jpg");
  background-size: contain;
  box-shadow: inset 0 0 50px #000;
  transition: 0.4s;
}

.section_blurred_img-container {
  display: flex;
  justify-content: center;
  width: 100%;
  min-height: 100vh;
  backdrop-filter: blur(25px);
  background-image: linear-gradient(to bottom, rgba(0,0,0,0.25), rgba(0,0,0,0.75));
}

.section_blurred_img-inner {
  background-image: url("../assets/images/cold-bg.jpg");
  background-size: cover;
  width: 360px;
  transition: 0.4s;
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
    margin: 1.75rem 3.5rem;
    box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
    user-select: none;
  }
  div:last-child {
    color: #FFF;
    font-size: 48px;
    font-weight: 700;
    font-style: italic;
    text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
    margin-left: 7.5rem;
  }
}
</style>