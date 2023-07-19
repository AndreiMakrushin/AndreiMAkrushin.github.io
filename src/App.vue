<script setup>
import { ref } from 'vue'

const arr = ref([
  {
    name: 'foo1',
    value: 'bar1'
  },
  {
    name: 'foo2',
    value: 'bar2'
  }
])

const rename = ref('')
const renameIndex = ref(null)

const redact = () => {
  if (renameIndex.value !== null) {
    arr.value[renameIndex.value].value = rename.value
  }
}
function convertArrayToObject(array) {
  const result = {};
  for (const item of array) {
    result[item.id] = item.count;
  }
  return result;
}

const resources = [
  {
    id: 1,
    count: 13,
  },
  {
    id: 2,
    count: 5,
  },
  {
    id: 3,
    count: 24,
  },
  {
    id: 4,
    count: 101,
  },
  {
    id: 5,
    count: 72,
  },
  {
    id: 6,
    count: 64,
  },
  {
    id: 7,
    count: 305,
  },
  {
    id: 8,
    count: 67,
  },
  {
    id: 9,
    count: 95,
  },
  {
    id: 10,
    count: 21,
  },
  {
    id: 11,
    count: 37,
  },
];

const result = convertArrayToObject(resources);
console.log(result);

</script>

<template>
  <div>
    <div class="container">
      <div class="content-container">
        <div class="rename-container">
          <input type="text" v-model="rename" class="rename-input" />
          <button @click="redact" class="rename-button">Редактировать</button>
        </div>

        <div v-for="(val, index) in arr" :key="index" class="value-container">
          <div
            class="value-item"
            @click="rename = val.value; renameIndex = index"
          >
            <span class="value-name">{{ val.name }}</span>
            <span class="value-value">{{ val.value }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.container {
  width: 100vw;
  font-family: 'poppins';
  background-color: black;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.content-container {
  
  border: 2px solid white;
  border-radius: 20px;
  text-align: center;
  background-color: black;
  color: white;
  padding: 2rem;
}

.rename-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 1rem;
}

.rename-input {
  margin-bottom: 5px;
  text-align: center;
  border: none;
  border-radius: 20px;
  width: 100%;
  font-size: 25px;
  margin-right: 1rem;
}

.rename-button {
  margin-top: 15px;
  border-radius: 20px;
  background-color: white;
  color: black;
  padding: 0.5rem 1rem;
  border: none;
  cursor: pointer;
}

.value-container {
  border-radius: 20px;
  padding: 7px;
  border: 2px solid white;
  margin-top: 2rem;
  margin-bottom: 1rem;
}

.value-item {
  cursor: pointer;
}

.value-name,
.value-value {
  
  width: 100%;
  margin-left: 5px;
  color: white;
}

.value-name {
  font-weight: bold;
}

</style>
