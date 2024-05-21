<template>
    <div v-if="infoJurusan">
      <slot :infoJurusan="infoJurusan"></slot>
      <button @click="kirimInfoJurusan">Pilih {{ infoJurusan.nama }}</button>
      <p v-if="pesanTerimaKasih" class="thank-you-message">Terimakasih semoga Kuat Sampai Tamat</p>
    </div>
  </template>
  
  <script setup>
  import { watch, ref } from 'vue';
  
  const props = defineProps({
    jurusan: String,
  });
  
  const emit = defineEmits(['info-jurusan']);
  
  const infoJurusan = ref(null);
  const pesanTerimaKasih = ref(false);
  
  const jurusanData = {
    TKJ: {
      nama: 'TKJ (Teknik Komputer dan Jaringan)',
      deskripsi: 'Jurusan yang mempelajari tentang komputer dan jaringan.',
    },
    TMI: {
      nama: 'TMI (Teknik Mesin Industri)',
      deskripsi: 'Jurusan yang mempelajari tentang mesin-mesin industri.',
    },
    TOI: {
      nama: 'TOI (Teknik Otomasi Industri)',
      deskripsi: 'Jurusan yang mempelajari tentang otomasi dalam industri.',
    },
  };
  
  watch(
    () => props.jurusan,
    (jurusanBaru) => {
      infoJurusan.value = jurusanData[jurusanBaru] || null;
      pesanTerimaKasih.value = false; // Reset pesan terima kasih setiap kali jurusan berubah
    }
  );
  
  const kirimInfoJurusan = () => {
    if (infoJurusan.value) {
      emit('info-jurusan', infoJurusan.value.nama);
      pesanTerimaKasih.value = true;
    }
  };
  </script>
  
  <style scoped>
  .thank-you-message {
    color: green;
    margin-top: 10px;
  }
  </style>
  