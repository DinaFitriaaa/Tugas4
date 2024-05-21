<template>
    <div>
      <h2>Pilih Jurusan</h2>
      <button @click="pilihJurusan('TKJ')">TKJ</button>
      <button @click="pilihJurusan('TMI')">TMI</button>
      <button @click="pilihJurusan('TOI')">TOI</button>
      <GrandChildComponent :jurusan="jurusanTerpilih" @info-jurusan="kirimInfoJurusan">
        <template #default="{ infoJurusan }">
          <slot :infoJurusan="infoJurusan"></slot>
        </template>
      </GrandChildComponent>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import GrandChildComponent from './GrandChildComponent.vue';
  
  const jurusanTerpilih = ref('');
  
  const pilihJurusan = (jurusan) => {
    jurusanTerpilih.value = jurusan;
  };
  
  const kirimInfoJurusan = (infoJurusan) => {
    emit('jurusan-dipilih', infoJurusan);
  };
  </script>
  