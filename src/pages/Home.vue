<template>
  <div class="grid place-items-center">
    <div id="home-app" class="bg-primary w-full md:hidden">
      <div class="content">
        <div v-if="!hasTakenQueue">
          <p class="pt-6 text-white text-center">Selamat Datang<span class="font-bold"> Afif,</span></p>
          <div class="w-full px-8">
            <div class="bg-white w-full max-w-md m-auto mt-6 text-primary rounded-lg">
              <div class="bg-secondary rounded-t">
                <p class="p-6 font-bold text-center text-xl text-white">ANTRIAN SAAT INI</p>
              </div>
              <p class="p-12 text-6xl font-bold text-center">09</p>
              <hr class="h-px border-0 bg-gray-light">
              <p class="p-3 text-center"><span class="font-bold">13</span> Pasien Sedang Antri</p>
            </div>
          </div>

          <div class="bg-white mt-16 p-4 rounded-t-3xl">
            <p class="text-center text-primary font-bold text-lg">AMBIL NOMOR ANTRIAN</p>
            <p class="text-primary mt-2 sm:text-center">Ambil nomor antrian di sini selama jam operasional klinik dan
              <span class="font-bold">datang sesuai waktu yang ditentukan.</span>
            </p>
            <div class="bg-secondary flex rounded items-center justify-center p-4 mt-4 gap-10 max-w-md m-auto">
              <img src="../assets/antrian.svg" alt="">
              <button @click="confirmQueue" class="bg-white text-primary py-2 px-6 rounded font-bold">
                Ambil Antrian
              </button>
            </div>

            <div v-if="showConfirmDialog"
              class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-50 z-30">
              <div class="bg-white p-6 m-6 w-full max-w-md rounded-lg shadow-lg">
                <p class="text-gray font-bold text-lg">Konfirmasi</p>
                <hr class="my-2 h-px border-0 bg-gray-light">
                <p class="text-gray font-semibold mt-4">Apakah Anda yakin ingin mengambil nomor antrian?</p>
                <div class="flex justify-end gap-4 mt-4">
                  <button @click="showConfirmDialog = false"
                    class="bg-gray-light px-4 py-2 text-gray rounded font-bold">Batal</button>
                  <button @click="takeQueue" class="bg-secondary text-white px-4 py-2 rounded font-bold">Daftar</button>

                </div>
              </div>
            </div>

            <div v-if="loading" class="fixed inset-0 flex items-center justify-center bg-white z-30">
              <Spinner />
            </div>

            <div class="flex flex-col items-center w-full pt-2 pb-4">
              <hr class="text-primary mt-2 w-2/4 h-px border-0 bg-gray-light">
              <hr class="text-primary mt-2 w-3/4 h-px border-0 bg-gray-light">
              <hr class="text-primary mt-2 w-full h-px border-0 bg-gray-light">
              <Information class="mt-4" />
            </div>
          </div>
        </div>

        <div v-else>
          <div id="home-antrian" class="bg-primary">
            <p class="pt-6 text-white text-center"><span class="font-bold">Berhasil</span> Ambil Nomor Antrian</p>
            <div class="bg-white w-11/12 m-auto mt-6 text-primary rounded-lg">
              <div class="bg-secondary">
                <p class="p-6 font-bold text-center text-xl text-white">NOMOR ANTRIAN ANDA</p>
              </div>
              <hr>
              <p class="p-12 text-6xl font-bold text-center">{{ queueNumber }}</p>
              <hr>
              <p class="p-3 text-center">Menunggu <span class="font-bold">{{ waitingPatients }}</span> Antrian Pasien
              </p>
            </div>
            <div class="px-4 mt-4">
              <p class="text-white">Anda telah <span class="font-bold"> berhasil mendapatkan nomor antrian </span>
                silahkan tunjukkan ke petugas yang ada.</p>
            </div>
            <div class="bg-white mt-4 p-4 rounded-t-3xl pb-16">
              <div class="bg-pure-white shadow-lg w-11/12 m-auto mt-6 text-primary rounded-lg">
                <div class="bg-primary">
                  <p class="p-6 font-bold text-center text-xl text-white">ANTRIAN SAAT INI</p>
                </div>
                <p class="p-12 text-6xl font-bold text-center">{{ queueNumber }}</p>
                <hr class="h-px border-0 bg-gray-light">
                <p class="p-3 text-center">Menunggu <span class="font-bold">{{ waitingPatients }}</span> Antrian Pasien
                </p>
              </div>
              <p class="text-gray mt-4">Nomor Antrian yang telah didapatkan akan <span class="font-bold"> di hapus
                  setelah 1 x 24 jam </span></p>
              <Information class="mt-4" />
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="hidden md:flex w-full flex-col pl-36 py-4 pr-4">
      <div class="content bg-primary p-4 rounded">
        <div v-if="!hasTakenQueue">
          <p class="pt-6 text-white text-center">Selamat Datang<span class="font-bold"> Afif,</span></p>
          <div class="max-w-2xl m-auto mt-6 text-primary rounded-lg bg-white">
            <div class="bg-secondary rounded-t">
              <p class="p-6 font-bold text-center text-xl text-white">ANTRIAN SAAT INI</p>
            </div>
            <p class="p-12 text-6xl font-bold text-center">09</p>
            <hr class="h-px border-0 bg-gray-light">
            <p class="p-3 text-center"><span class="font-bold">13</span> Pasien Sedang Antri</p>
          </div>

          <div class="bg-white mt-16 p-4 rounded-t-3xl py-8">
            <p class="text-center text-primary font-bold text-lg">AMBIL NOMOR ANTRIAN</p>

            <div
              class="bg-secondary md:px-16 w-11/12 flex rounded-xl items-center flex-col justify-center p-4 py-10 m-auto mt-4 gap-10">
              <img src="../assets/antrian.svg" alt="">
              <p class="text-white mt-2 text-center">Ambil nomor antrian di sini selama jam operasional
                klinik dan
                <span class="font-bold">datang sesuai waktu yang ditentukan.</span>
              </p>
              <button @click="confirmQueue" class="bg-white text-primary py-2 px-6 rounded font-bold">
                Ambil Antrian
              </button>
            </div>

            <div v-if="showConfirmDialog"
              class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-50 z-30">
              <div class="bg-white p-6 m-6 w-full max-w-md rounded-lg shadow-lg">
                <p class="text-gray font-bold text-lg">Konfirmasi</p>
                <hr class="my-2 h-px border-0 bg-gray-light">
                <p class="text-gray font-semibold mt-4">Apakah Anda yakin ingin mengambil nomor antrian?</p>
                <div class="flex justify-end gap-4 mt-4">
                  <button @click="showConfirmDialog = false"
                    class="bg-gray-light px-4 py-2 text-gray rounded font-bold">Batal</button>
                  <button @click="takeQueue" class="bg-secondary text-white px-4 py-2 rounded font-bold">Daftar</button>

                </div>
              </div>
            </div>

            <div v-if="loading" class="fixed inset-0 flex items-center justify-center bg-white z-30">
              <Spinner />
            </div>

            <div class="flex flex-col items-center w-full m-auto pt-2 pb-4">
              <hr class="text-primary mt-2 w-6/12 h-px border-0 bg-gray-light">
              <hr class="text-primary mt-2 w-8/12 h-px border-0 bg-gray-light">
              <hr class="text-primary mt-2 w-10/12 h-px border-0 bg-gray-light">
              <Information class="mt-4 !bg-primary !text-white !w-11/12 py-6 mt-6" />
            </div>
          </div>
        </div>

        <div v-else>
          <div id="home-antrian" class="bg-primary">
            <p class="pt-6 text-white text-center"><span class="font-bold">Berhasil</span> Ambil Nomor Antrian</p>
            <div class="bg-white max-w-2xl w-full m-auto mt-6 text-primary rounded-lg">
              <div class="bg-secondary">
                <p class="p-6 font-bold text-center text-xl text-white">NOMOR ANTRIAN ANDA</p>
              </div>
              <hr>
              <p class="p-12 text-6xl font-bold text-center">{{ queueNumber }}</p>
              <hr>
              <p class="p-3 text-center">Menunggu <span class="font-bold">{{ waitingPatients }}</span> Antrian Pasien
              </p>
            </div>
            <div class="px-4 mt-4">
              <p class="text-white text-center my-6">Anda telah <span class="font-bold"> berhasil mendapatkan nomor
                  antrian </span>
                silahkan tunjukkan ke petugas yang ada.</p>
            </div>
            <div class="bg-white mt-4 p-4 rounded-t-3xl pb-16">
              <div class="bg-pure-white shadow-lg w-full m-auto mt-6 text-primary rounded-lg">
                <div class="bg-primary rounded-t">
                  <p class="p-6 font-bold text-center text-xl text-white">ANTRIAN SAAT INI</p>
                </div>
                <p class="p-12 text-6xl font-bold text-center">{{ queueNumber }}</p>
                <hr class="h-px border-0 bg-gray-light">
                <p class="p-3 text-center">Menunggu <span class="font-bold">{{ waitingPatients }}</span> Antrian Pasien
                </p>
              </div>
              <p class="text-gray mt-6 text-center">Nomor Antrian yang telah didapatkan akan <span class="font-bold"> di
                  hapus
                  setelah 1 x 24 jam </span></p>
              <Information class="mt-4 !bg-primary !text-white w-8/12 py-6 mt-6" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
import Information from '../components/Information.vue';
import Spinner from '../components/Spinner.vue';
import RegisterCard from '../components/RegisterCard.vue';
import NavbarTop from '../components/NavbarTop.vue';

export default {
  name: 'Home',
  components: {
    Information,
    Spinner,
    RegisterCard
  },
  setup() {
    const showConfirmDialog = ref(false);
    const loading = ref(false);
    const hasTakenQueue = ref(false);
    const queueNumber = ref('');
    const waitingPatients = ref(3);

    const confirmQueue = () => {
      showConfirmDialog.value = true;
    };

    const takeQueue = () => {
      showConfirmDialog.value = false;
      loading.value = true;

      setTimeout(() => {
        loading.value = false;
        hasTakenQueue.value = true;
        queueNumber.value = Math.floor(Math.random() * 100) + 1;
      }, 3000);
    };

    return {
      showConfirmDialog,
      loading,
      hasTakenQueue,
      queueNumber,
      waitingPatients,
      confirmQueue,
      takeQueue
    };
  }
};
</script>