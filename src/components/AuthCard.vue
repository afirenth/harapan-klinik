<template>
    <div class="p-4 sm:p-12 bg-pure-white shadow-xl rounded-lg">
        <p class="text-lg font-bold text-primary text-center">Selamat datang di Harapan Klinik</p>
        <p class="text-primary text-center mt-2">Kesehatan Anda, prioritas kami. Antri lebih mudah, pelayanan lebih
            cepat.</p>

        <div class="mt-4 space-y-2">
            <hr class="text-primary mt-2 w-2/4 m-auto" />
            <hr class="text-primary mt-2 w-3/4 m-auto" />
            <hr class="text-primary mt-2 w-full m-auto" />
        </div>

        <p class="mt-4 text-primary sm:text-center">
            Silahkan <span class="font-bold">Login</span> untuk melanjutkan ke Aplikasi
        </p>

        <LoginCard />

        <p class="mt-4 text-primary sm:text-center">
            Belum punya akun? <span class="font-bold">Daftar Sekarang!</span>
        </p>

        <RegisterCard />
    </div>
</template>

<script>
import LoginCard from './LoginCard.vue';
import RegisterCard from './RegisterCard.vue';

export default {
    name: 'AuthCard',
    components: {
        LoginCard,
        RegisterCard
    }
};
</script>