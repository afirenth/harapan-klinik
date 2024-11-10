<template>
    <div id="home-antrian" class="bg-primary">
        <p class="pt-6 text-white text-center"><span class="font-bold">Berhasil</span> Ambil Nomor Antrian</p>
        <div class="bg-white w-full max-w-md m-auto mt-6 text-primary rounded-lg">
            <div class="bg-secondary rounded-t">
                <p class="p-6 font-bold text-center text-xl text-white">NOMOR ANTRIAN ANDA</p>
            </div>
            <hr>
            <!-- Menangani tampilan nomor antrian jika sudah ada -->
            <p v-if="queueNumber" class="p-12 text-6xl font-bold text-center">{{ queueNumber }}</p>
            <p v-else class="p-12 text-6xl font-bold text-center">Antrian Belum Tersedia</p>
            <hr>
            <p class="p-3 text-center">Menunggu <span class="font-bold">{{ waitingPatients }}</span> Antrian Pasien</p>
        </div>
        <div class="px-4 mt-4">
            <p class="text-white md:text-center">Anda telah <span class="font-bold"> berhasil mendapatkan nomor antrian
                </span>
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
            <p class="text-gray mt-4 md:text-center">Nomor Antrian yang telah didapatkan akan <span class="font-bold">
                    di hapus
                    setelah 1 x 24 jam </span></p>
            <InformationCard class="mt-4 !bg-primary !text-white w-8/12 py-6 mt-6" />
        </div>
    </div>
</template>

<script>
import InformationCard from './InformationCard.vue';

export default {
    name: 'QueueDetails',
    components: { InformationCard },
    props: {
        queueNumber: {
            type: Number,
            required: true
        },
        waitingPatients: {
            type: Number,
            required: true
        }
    }
};
</script>