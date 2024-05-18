<!-- ParentComponent.vue -->
<template>
  <div>
    <nav class="navbar">
      <button @click="activeChild = 1">Child 1</button>
    </nav>
    <ChildComponent1 v-if="activeChild === 1" @dataSent="handleDataFromChild1">
      <h2>Konten yang ditampilkan:</h2>
      <p>Ini adalah konten yang akan disisipkan ke dalam ChildComponent1</p>
    </ChildComponent1>
    </div>
</template>

<script setup>
import ChildComponent1 from './components/ChildComponent1.vue';
import { ref } from 'vue';

const contentFromChild1 = ref('');
const activeChild = ref(1);

const handleDataFromChild1 = (data) => {
  contentFromChild1.value = data;
  activeChild.value = 1;
};
</script>

<style>

body {
  background-image: url(1.jpg);
}
h2 {
  color: white;
}

p {
  color: white;
}
.navbar {
  padding: 10px;

}

.navbar button {
  padding: 8px 12px;
  margin-right: 10px;
  background-color: #fff;
  color:black;
  border: none;
  border-radius: 5px;
  cursor: pointer;

}
</style>
