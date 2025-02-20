<script setup>
import {reactive} from 'vue'
import {GetRandomImageUrl} from '../../wailsjs/go/main/App'


const data = reactive({
  showBreedPhotos: false,
  imageUrl: "",
})

function getRandomImageUrl() {
    data.imageUrl = "";
    data.showBreedPhotos = false;
    GetRandomImageUrl().then((result) => (data.imageUrl = result));
    data.showBreedPhotos = true;
  }


</script>

<template>
  <main>
    <div id="input" class="input-box">
      <button class="btn" @click="getRandomImageUrl">
        Random
      </button>

        <div v-if="data.showBreedPhotos">
          <img width="500px" :src="data.imageUrl" alt="Random dog" />
        </div>

    </div>
  </main>
</template>

<style scoped>
.result {
  height: 20px;
  line-height: 20px;
  margin: 1.5rem auto;
}

.input-box .btn {
  width: 60px;
  height: 30px;
  line-height: 30px;
  border-radius: 3px;
  border: none;
  margin: 0 0 0 20px;
  padding: 0 8px;
  cursor: pointer;
}

.input-box .btn:hover {
  background-image: linear-gradient(to top, #cfd9df 0%, #e2ebf0 100%);
  color: #333333;
}

.input-box .input {
  border: none;
  border-radius: 3px;
  outline: none;
  height: 30px;
  line-height: 30px;
  padding: 0 10px;
  background-color: rgba(240, 240, 240, 1);
  -webkit-font-smoothing: antialiased;
}

.input-box .input:hover {
  border: none;
  background-color: rgba(255, 255, 255, 1);
}

.input-box .input:focus {
  border: none;
  background-color: rgba(255, 255, 255, 1);
}
</style>
