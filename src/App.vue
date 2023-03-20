<template>
  <div class="container my-4">
    <h2 class="fw-bold">Lucky Numbers</h2>
    <div class="row mt-4">
      <div class="col-4">
        <div class="card shadow-sm">
          <div class="card-body">
            <h5 class="card-title">First Number</h5>
            <p class="card-text">{{ x }}</p>
          </div>
        </div>
      </div>
      <div class="col-4">
        <div class="card shadow-sm">
          <div class="card-body">
            <h5 class="card-title">Second Number</h5>
            <p class="card-text">{{ y }}</p>
          </div>
        </div>
      </div>
      <div class="col-4">
        <div class="card shadow-sm">
          <div class="card-body">
            <h5 class="card-title">Third Number</h5>
            <p class="card-text">{{ z }}</p>
          </div>
        </div>
      </div>
    </div>
    <div class="d-flex">
      <button class="btn btn-success mt-4 form-control" @click="generate">Generate</button>
    </div>
  </div>
  <RouterView />
</template>

<script>
import { RouterView } from 'vue-router'
import { ref } from 'vue'
  export default {
    setup() {
      let x = ref(0);
      let y = ref(0);
      let z = ref(0);
      const date = new Date();
      const clickCounter = ref(0);

      const generate = () => {
        let day = Number(date.getDate());
        let month = Number(date.getMonth());
        x.value = Math.floor(Math.random() * 4) * day;
        y.value = Math.floor(Math.random() * 10) * month + Number(clickCounter.value);
        z.value = Math.floor(Math.random() * 3) * day + Number(clickCounter.value);
        clickCounter += 1;
      }
      return {
        x,
        y,
        z,
        date,
        generate
      }
    }
  }
</script>


<style scoped>

</style>
