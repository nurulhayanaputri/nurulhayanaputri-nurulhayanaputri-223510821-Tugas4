<template>
  <div>
    <button @click="sendData">Kirim Data dari Child 1</button>
    <slot></slot>
    <table class="table">
      <thead>
        <tr>
          <th>Nama</th>
          <th>NIM</th>
          <th>Tanggal Lahir</th>
          <th>Alamat</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="mahasiswa in mahasiswaList" :key="mahasiswa.nim">
          <td>{{ mahasiswa.nama }}</td>
          <td>{{ mahasiswa.nim }}</td>
          <td>{{ mahasiswa.tanggal_lahir }}</td>
          <td>{{ mahasiswa.alamat }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { defineEmits, ref } from 'vue';

const emit = defineEmits(['dataSent']);

const mahasiswaList = ref([]);

const sendData = () => {
  const data = [
    { nama: 'Fadia Hervan', nim: '225454', tanggal_lahir: '01-02-2004', alamat: 'Jl. Melati No. 123' },
    { nama: 'Dhea Sri', nim: '655521', tanggal_lahir: '08-07-2001', alamat: 'Jl. Mawar No. 456' }
  ];
  mahasiswaList.value = data;
  emit('dataSent', data);
};

const handleDataFromChild1 = (data) => {
  mahasiswaList.value = data;
};
</script>

<style scoped>
.table {
  width: 100%;
  border-collapse: collapse;

}

.table th,
.table td {
  padding: 8px;
  border-bottom: 1px solid #ddd;
  text-align: left;
  color: white;

}

.table th {
  color: white;

}

.table tbody tr:nth-child(even) {
  color: white;
}
</style>