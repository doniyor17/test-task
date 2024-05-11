<script setup>
import { onMounted, ref } from 'vue';

const horCols = ref([]);


function randomize() { 
  const randomHundred = Math.floor(Math.random() * 100);
  const random = Math.floor(Math.random() * 10);
  horCols.value = [];
  for (let i = 0; i < randomHundred; i++) {
    let newArr = [];
    for (let j = 0; j < random; j++) {
      const num = Math.floor(Math.random() * 100);
      if (num % 3 === 1) {
        newArr.push('-');
      } else {
        newArr.push(Math.floor(Math.random() * 100));
      }
    }
    horCols.value.push(newArr);
  }
}



onMounted(() => {
  randomize();
})
</script>

<template>
  <div class="verticals">
    <div v-for="cols in horCols" :key="cols" class="">
      <div v-for="col in cols" :key="col" class="horizontals border">
        <div :class="{ invisible: col === '-' }">
          {{ col }}
        </div>
      </div>
    </div>
  </div>
  <button @click="randomize">
    Generate
  </button>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
.invisible {
  visibility: hidden;
}
.border {
  border: 1px solid white;
  padding: 5px;
  transition: all ease-in-out .1s;
  cursor: pointer;
}
.border:hover{
  scale: 0.8;
  border-radius: 5px;
}
.verticals {
  display: flex;
  text-align: center;
  margin-bottom: 15px;
}
</style>
