<template>
  <div class="grid place-items-center min-h-screen">
    <div class="relative w-full md:hidden">
      <div class="absolute top-0 w-full h-96 bg-primary rounded-b-xl z-10"></div>
      <div class="absolute top-0 w-full h-full bg-white z-0"></div>
      <div class="relative z-20 pt-12 px-6 sm:px-12">
        <img src="../assets/logo-small.svg" alt="" class="m-auto">
        <p class="text-white text-lg mt-6 font-semibold">Menu <span class="font-bold">Daftar</span></p>
        <p class="text-white">Silahkan Daftar untuk melanjutkan ke dalam Aplikasi Harapan Klinik.</p>

        <RegisterForm @submit.prevent="handleRegister" />

        <p class="mt-8 text-primary sm:text-center">Sudah punya akun? <span class="font-bold">Login Sekarang!</span></p>
        <LoginCard />
        <InformationCard class="mt-8" />
      </div>
    </div>
    <div class="hidden md:flex my-16 h-full lg:h-fit w-full lg:w-10/12 bg-primary lg:rounded-lg items-center">
      <div class="flex-1 p-8"><img src="../assets/logo-big.svg" alt="" class="mb-12 mx-auto">
        <InformationCard />

        <p class="mt-8 text-white text-center">Sudah punya akun? <span class="font-bold">Login Sekarang!</span></p>
        <LoginCard class="bg-secondary" />
      </div>
      <div class="flex-1 p-8">
        <div class="relative z-20">
          <p class="text-white text-lg font-semibold">Menu <span class="font-bold">Daftar</span></p>
          <p class="text-white">Silahkan Daftar untuk melanjutkan ke dalam Aplikasi Harapan Klinik.</p>

          <RegisterForm @submit.prevent="handleRegister" />

        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import LoginCard from '../components/LoginCard.vue';
import InformationCard from '../components/InformationCard.vue';
import RegisterForm from '../components/RegisterForm.vue';

export default {
  name: 'Register',
  components: {
    LoginCard,
    InformationCard,
    RegisterForm,
  },
  setup() {
    const router = useRouter();

    const handleRegister = () => {
      router.push('/home');
    };

    return {
      handleRegister,
    };
  },
};
</script>
