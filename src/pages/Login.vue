<template>
  <div class="grid place-items-center min-h-screen">
    <div class="relative w-full md:hidden">
      <div class="absolute top-0 w-full h-96 bg-primary rounded-b-xl z-10"></div>
      <div class="absolute top-0 w-full h-full bg-white z-0"></div>
      <div class="relative z-20 pt-12 px-6 sm:px-12">
        <img src="../assets/logo-small.svg" alt="" class="m-auto">
        <p class="text-white text-lg mt-6 font-semibold">Menu <span class="font-bold">Login</span></p>
        <p class="text-white">Silahkan Login untuk melanjutkan ke dalam Aplikasi Harapan Klinik.</p>

        <form @submit.prevent="handleLogin">
          <div class="bg-pure-white shadow-lg rounded-lg p-5 mt-6">
            <div class="bg-white flex items-center rounded p-2">
              <img src="../assets/person.svg" alt="" class="w-8 h-8">
              <input required type="text" placeholder="Email / No. HP" v-model="email"
                class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
            </div>
            <div class="mt-4 bg-white flex items-center rounded relative p-2">
              <img src="../assets/lock.svg" alt="" class="w-8 h-8">
              <input required :type="showPassword ? 'text' : 'password'" placeholder="Password" v-model="password"
                class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
              <img :src="showPassword ? eyeOpenIcon : eyeClosedIcon" alt=""
                class="w-6 h-6 absolute right-3 cursor-pointer" @click="togglePasswordVisibility" />
            </div>
            <button type="submit" class="w-full bg-secondary mt-6 text-white p-2 rounded font-bold">Login
              Sekarang</button>
            <p class="text-primary text-center mt-4 italic underline">Lupa password?</p>
          </div>
        </form>

        <p class="mt-8 text-primary sm:text-center">Belum punya akun? <span class="font-bold">Daftar Sekarang!</span>
        </p>
        <RegisterCard />
        <Information class="mt-8" />
      </div>
    </div>

    <div class="hidden md:flex w-full h-full lg:h-fit lg:w-10/12 bg-primary lg:rounded-lg items-center">
      <div class="flex-1 p-8"><img src="../assets/logo-big.svg" alt="" class="mb-12 mx-auto">
        <Information />
      </div>
      <div class="flex-1 p-8">
        <div class="relative z-20">
          <p class="text-white text-lg mt-6 font-semibold">Menu <span class="font-bold">Login</span></p>
          <p class="text-white">Silahkan Login untuk melanjutkan ke dalam <br> Aplikasi.</p>

          <form @submit.prevent="handleLogin">
            <div class="bg-pure-white shadow-lg rounded-lg p-5 mt-6">
              <div class="bg-white flex items-center rounded p-2">
                <img src="../assets/person.svg" alt="" class="w-8 h-8">
                <input required type="text" placeholder="Email / No. HP" v-model="email"
                  class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
              </div>
              <div class="mt-4 bg-white flex items-center rounded relative p-2">
                <img src="../assets/lock.svg" alt="" class="w-8 h-8">
                <input required :type="showPassword ? 'text' : 'password'" placeholder="Password" v-model="password"
                  class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
                <img :src="showPassword ? eyeOpenIcon : eyeClosedIcon" alt=""
                  class="w-6 h-6 absolute right-3 cursor-pointer" @click="togglePasswordVisibility" />
              </div>
              <button type="submit" class="w-full bg-primary mt-6 text-white p-2 rounded font-bold">Login
                Sekarang</button>
              <p class="text-primary text-center mt-4 italic underline">Lupa password?</p>
            </div>
          </form>

          <p class="mt-8 text-white sm:text-center">Belum punya akun? <span class="font-bold">Daftar
              Sekarang!</span>
          </p>
          <RegisterCard />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import RegisterCard from '../components/RegisterCard.vue';
import Information from '../components/Information.vue';

import eyeOpenIcon from '../assets/eye-open.svg';
import eyeClosedIcon from '../assets/eye-closed.svg';

export default {
  name: 'Login',
  components: {
    RegisterCard,
    Information
  },
  setup() {
    const email = ref('');
    const password = ref('');
    const showPassword = ref(false);
    const router = useRouter();

    const handleLogin = () => {
      router.push('/home');
    };

    const togglePasswordVisibility = () => {
      showPassword.value = !showPassword.value;
    };

    return {
      email,
      password,
      showPassword,
      eyeOpenIcon,
      eyeClosedIcon,
      handleLogin,
      togglePasswordVisibility,
    };
  },
};
</script>
