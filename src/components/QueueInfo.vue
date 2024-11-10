<template>
    <div class="w-full px-8">
        <p class="text-white text-center mt-6">Selamat Datang <span class="font-bold"> Afif,</span></p>

        <div class="bg-white w-full max-w-md m-auto mt-6 text-primary rounded-lg">
            <div class="bg-secondary rounded-t">
                <p class="p-6 font-bold text-center text-xl text-white">ANTRIAN SAAT INI</p>
            </div>
            <!-- Menangani kasus nomor antrian kosong atau belum ada -->
            <p v-if="!queueNumber" class="p-12 text-6xl font-bold text-center">09</p>
            <p v-else class="p-12 text-6xl font-bold text-center">{{ queueNumber }}</p>
            <hr class="h-px border-0 bg-gray-light">
            <p class="p-3 text-center"><span class="font-bold">{{ waitingPatients }}</span> Pasien Sedang Antri</p>
        </div>

        <div class="bg-white mt-16 p-4 rounded-t-3xl">
            <p class="text-center text-primary font-bold text-lg">AMBIL NOMOR ANTRIAN</p>
            <p class="text-primary mt-2 sm:text-center">Ambil nomor antrian di sini selama jam operasional klinik dan
                <span class="font-bold">datang sesuai waktu yang ditentukan.</span>
            </p>
            <div class="bg-secondary flex rounded items-center justify-center p-4 mt-4 gap-10 max-w-md m-auto">
                <img src="../assets/antrian.svg" alt="" />
                <!-- Tombol untuk mengambil antrian -->
                <button @click="$emit('confirmQueue')" class="bg-white text-primary py-2 px-6 rounded font-bold">
                    Ambil Antrian
                </button>
            </div>
            <InformationCard class="mt-4 !bg-primary !text-white w-8/12 py-6 mt-6" />
        </div>
    </div>
</template>

<script>
import InformationCard from './InformationCard.vue';

export default {
    name: 'QueueInfo',
    components: {
        InformationCard
    },
    props: {
        queueNumber: {
            type: Number,
            default: null
        },
        waitingPatients: {
            type: Number,
            default: 0
        }
    }
};
</script>