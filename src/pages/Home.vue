<template>
  <div class="grid place-items-center">
    <div id="home-app" class="bg-primary w-full md:hidden">
      <div class="content">
        <!-- Menampilkan QueueInfo jika antrian belum diambil -->
        <QueueInfo v-if="!hasTakenQueue" :queueNumber="queueNumber" :waitingPatients="waitingPatients"
          @confirmQueue="confirmQueue" />
        <!-- Menampilkan QueueDetails jika antrian sudah diambil -->
        <QueueDetails v-else :queueNumber="queueNumber" :waitingPatients="waitingPatients" />
      </div>
    </div>

    <div class="hidden md:flex w-full flex-col pl-36 py-4 pr-4">
      <div class="content bg-primary p-4 rounded">
        <!-- Menampilkan QueueInfo jika antrian belum diambil -->
        <QueueInfo v-if="!hasTakenQueue" :queueNumber="queueNumber" :waitingPatients="waitingPatients"
          @confirmQueue="confirmQueue" />
        <!-- Menampilkan QueueDetails jika antrian sudah diambil -->
        <QueueDetails v-else :queueNumber="queueNumber" :waitingPatients="waitingPatients" />
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
import QueueInfo from '../components/QueueInfo.vue';
import QueueDetails from '../components/QueueDetails.vue';
import InformationCard from '../components/InformationCard.vue';

export default {
  name: 'Home',
  components: {
    QueueInfo,
    QueueDetails,
    InformationCard
  },
  setup() {
    const hasTakenQueue = ref(false);
    const queueNumber = ref(null);  // Menggunakan null agar bisa dibedakan dengan nomor kosong
    const waitingPatients = ref(3);

    const confirmQueue = () => {
      // Mengubah kondisi untuk mengambil antrian
      hasTakenQueue.value = true;
      queueNumber.value = Math.floor(Math.random() * 100) + 1;  // Memberikan nomor antrian acak
    };

    return {
      hasTakenQueue,
      queueNumber,
      waitingPatients,
      confirmQueue
    };
  }
};
</script>
