<template>
  <div class="grid place-items-center min-h-screen">
    <!-- Tampilan Mobile -->
    <div class="relative w-full md:hidden">
      <div class="absolute top-0 w-full h-96 bg-primary rounded-b-xl z-10"></div>
      <div class="absolute top-0 w-full h-full bg-white z-0"></div>
      <div class="relative z-20 pt-12 px-6 sm:px-12">
        <img src="../assets/logo-small.svg" alt="" class="m-auto" />
        <p class="text-white text-lg mt-6 font-semibold">Menu <span class="font-bold">Login</span></p>
        <p class="text-white">Silahkan Login untuk melanjutkan ke dalam Aplikasi Harapan Klinik.</p>

        <LoginForm />

        <p class="mt-8 text-primary sm:text-center">Belum punya akun? <span class="font-bold">Daftar Sekarang!</span>
        </p>
        <RegisterCard />
        <InformationCard class="mt-8" />
      </div>
    </div>

    <!-- Tampilan Desktop -->
    <div class="hidden md:flex w-full h-full lg:h-fit lg:w-10/12 bg-primary lg:rounded-lg items-center">
      <div class="flex-1 p-8">
        <img src="../assets/logo-big.svg" alt="" class="mb-12 mx-auto" />
        <InformationCard />
      </div>
      <div class="flex-1 p-8">
        <div class="relative z-20">
          <p class="text-white text-lg mt-6 font-semibold">Menu <span class="font-bold">Login</span></p>
          <p class="text-white">Silahkan Login untuk melanjutkan ke dalam <br /> Aplikasi.</p>

          <LoginForm />

          <p class="mt-8 text-white sm:text-center">Belum punya akun? <span class="font-bold">Daftar Sekarang!</span>
          </p>
          <RegisterCard />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import LoginForm from '../components/LoginForm.vue';
import RegisterCard from '../components/RegisterCard.vue';
import InformationCard from '../components/InformationCard.vue';

export default {
  name: 'Login',
  components: {
    LoginForm,
    RegisterCard,
    InformationCard
  }
};
</script>
