<template>
  <div class="container">
    <h1>Jurusan SMK</h1>
    <p>Jurusan Terpilih: {{ jurusanTerpilih }}</p>
    <ChildComponent @jurusan-dipilih="perbaruiJurusan">
      <template #default="{ infoJurusan }">
        <div v-if="infoJurusan">
          <h2>{{ infoJurusan.nama }}</h2>
          <p>{{ infoJurusan.deskripsi }}</p>
        </div>
      </template>
    </ChildComponent>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import ChildComponent from './ChildComponent.vue';

const jurusanTerpilih = ref('');

const perbaruiJurusan = (jurusan) => {
  jurusanTerpilih.value = jurusan;
};
</script>
