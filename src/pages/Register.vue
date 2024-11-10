<template>
  <div class="grid place-items-center min-h-screen">
    <div class="relative w-full md:hidden">
      <div class="absolute top-0 w-full h-96 bg-primary rounded-b-xl z-10"></div>
      <div class="absolute top-0 w-full h-full bg-white z-0"></div>
      <div class="relative z-20 pt-12 px-6 sm:px-12">
        <img src="../assets/logo-small.svg" alt="" class="m-auto">
        <p class="text-white text-lg mt-6 font-semibold">Menu <span class="font-bold">Daftar</span></p>
        <p class="text-white">Silahkan Daftar untuk melanjutkan ke dalam Aplikasi Harapan Klinik.</p>

        <form @submit.prevent="handleRegister">
          <div class="bg-pure-white shadow-lg rounded-lg p-5 mt-6">
            <div class="bg-white flex items-center rounded p-2">
              <img src="../assets/person.svg" alt="" class="w-8 h-8">
              <input type="text" placeholder="Nama Lengkap" v-model="fullName" required
                class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
            </div>
            <div class="mt-4 bg-white flex items-center rounded p-2">
              <img src="../assets/email.svg" alt="" class="w-8 h-8">
              <input type="email" placeholder="Email" v-model="email" required
                class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
            </div>
            <div class="mt-4 bg-white flex items-center rounded p-2 relative">
              <img src="../assets/lock.svg" alt="" class="w-8 h-8">
              <input :type="showPassword ? 'text' : 'password'" placeholder="Password" v-model="password" required
                class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
              <img :src="showPassword ? eyeOpenIcon : eyeClosedIcon" alt=""
                class="w-6 h-6 absolute right-3 cursor-pointer" @click="togglePasswordVisibility" />
            </div>
            <div class="mt-4 bg-white flex items-center rounded p-2 relative">
              <img src="../assets/lock.svg" alt="" class="w-8 h-8">
              <input :type="showConfirmPassword ? 'text' : 'password'" placeholder="Konfirmasi Password"
                v-model="confirmPassword" required class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
              <img :src="showConfirmPassword ? eyeOpenIcon : eyeClosedIcon" alt=""
                class="w-6 h-6 absolute right-3 cursor-pointer" @click="toggleConfirmPasswordVisibility" />
            </div>
            <div class="mt-4 bg-white flex items-center rounded p-2">
              <img src="../assets/phone.svg" alt="" class="w-8 h-8">
              <input type="text" placeholder="No HP" v-model="phoneNumber" required
                class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
            </div>
            <div class="mt-4 bg-white flex items-center rounded p-2">
              <img src="../assets/date.svg" alt="" class="w-8 h-8">
              <input type="date" placeholder="Tanggal Lahir" v-model="birthDate" required
                class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
            </div>
            <div class="mt-4 bg-white flex items-center rounded p-2">
              <img src="../assets/location.svg" alt="" class="w-8 h-8">
              <input type="text" placeholder="Alamat" v-model="address" required
                class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
            </div>
            <div class="mt-4 flex text-gray">
              <p class="font-semibold">Jenis Kelamin: </p>
              <div class="flex gap-2 items-center ml-4">
                <input type="radio" id="pria" value="Pria" v-model="gender" required />
                <label for="pria">Pria</label>
              </div>
              <div class="flex gap-2 items-center ml-4">
                <input type="radio" id="wanita" value="Wanita" v-model="gender" required />
                <label for="wanita">Wanita</label>
              </div>
            </div>
            <button type="submit" class="w-full bg-secondary mt-4 text-white p-3 rounded font-bold">Daftar
              Sekarang</button>
          </div>
        </form>

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

          <!-- Tambahkan elemen <form> disini -->
          <form @submit.prevent="handleRegister">
            <div class="bg-pure-white shadow-lg rounded-lg p-5 mt-6">
              <div class="bg-white flex items-center rounded p-2">
                <img src="../assets/person.svg" alt="" class="w-8 h-8">
                <input type="text" placeholder="Nama Lengkap" v-model="fullName" required
                  class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
              </div>
              <div class="mt-4 bg-white flex items-center rounded p-2">
                <img src="../assets/email.svg" alt="" class="w-8 h-8">
                <input type="email" placeholder="Email" v-model="email" required
                  class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
              </div>
              <div class="mt-4 bg-white flex items-center rounded p-2 relative">
                <img src="../assets/lock.svg" alt="" class="w-8 h-8">
                <input :type="showPassword ? 'text' : 'password'" placeholder="Password" v-model="password" required
                  class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
                <img :src="showPassword ? eyeOpenIcon : eyeClosedIcon" alt=""
                  class="w-6 h-6 absolute right-3 cursor-pointer" @click="togglePasswordVisibility" />
              </div>
              <div class="mt-4 bg-white flex items-center rounded p-2 relative">
                <img src="../assets/lock.svg" alt="" class="w-8 h-8">
                <input :type="showConfirmPassword ? 'text' : 'password'" placeholder="Konfirmasi Password"
                  v-model="confirmPassword" required
                  class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
                <img :src="showConfirmPassword ? eyeOpenIcon : eyeClosedIcon" alt=""
                  class="w-6 h-6 absolute right-3 cursor-pointer" @click="toggleConfirmPasswordVisibility" />
              </div>
              <div class="mt-4 bg-white flex items-center rounded p-2">
                <img src="../assets/phone.svg" alt="" class="w-8 h-8">
                <input type="text" placeholder="No HP" v-model="phoneNumber" required
                  class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
              </div>
              <div class="mt-4 bg-white flex items-center rounded p-2">
                <img src="../assets/date.svg" alt="" class="w-8 h-8">
                <input type="date" placeholder="Tanggal Lahir" v-model="birthDate" required
                  class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
              </div>
              <div class="mt-4 bg-white flex items-center rounded p-2">
                <img src="../assets/location.svg" alt="" class="w-8 h-8">
                <input type="text" placeholder="Alamat" v-model="address" required
                  class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
              </div>
              <div class="mt-4 flex text-gray">
                <p class="font-semibold">Jenis Kelamin: </p>
                <div class="flex gap-2 items-center ml-4">
                  <input type="radio" id="pria" value="Pria" v-model="gender" required />
                  <label for="pria">Pria</label>
                </div>
                <div class="flex gap-2 items-center ml-4">
                  <input type="radio" id="wanita" value="Wanita" v-model="gender" required />
                  <label for="wanita">Wanita</label>
                </div>
              </div>
              <button type="submit" class="w-full bg-primary mt-4 text-white p-3 rounded font-bold">Daftar
                Sekarang</button>
            </div>
          </form>

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

import eyeOpenIcon from '../assets/eye-open.svg';
import eyeClosedIcon from '../assets/eye-closed.svg';

export default {
  name: 'Register',
  components: {
    LoginCard,
    InformationCard
  },
  setup() {
    const fullName = ref('');
    const email = ref('');
    const password = ref('');
    const confirmPassword = ref('');
    const phoneNumber = ref('');
    const birthDate = ref('');
    const address = ref('');
    const gender = ref('');

    const showPassword = ref(false);
    const showConfirmPassword = ref(false);
    const router = useRouter();

    const handleRegister = () => {
      router.push('/home');
    };

    const togglePasswordVisibility = () => {
      showPassword.value = !showPassword.value;
    };

    const toggleConfirmPasswordVisibility = () => {
      showConfirmPassword.value = !showConfirmPassword.value;
    };

    return {
      fullName,
      email,
      password,
      confirmPassword,
      phoneNumber,
      birthDate,
      address,
      gender,
      showPassword,
      showConfirmPassword,
      eyeOpenIcon,
      eyeClosedIcon,
      handleRegister,
      togglePasswordVisibility,
      toggleConfirmPasswordVisibility,
    };
  },
};
</script>
