<template>
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
            <button type="submit" class="w-full bg-secondary mt-4 text-white p-3 rounded font-bold">Daftar
                Sekarang</button>
        </div>
    </form>
</template>

<script>
import eyeOpenIcon from '../assets/eye-open.svg';
import eyeClosedIcon from '../assets/eye-closed.svg';

export default {
    name: 'RegisterForm',
    props: ['handleRegister'],
    data() {
        return {
            fullName: '',
            email: '',
            password: '',
            confirmPassword: '',
            phoneNumber: '',
            birthDate: '',
            address: '',
            gender: '',
            showPassword: false,
            showConfirmPassword: false,
            eyeOpenIcon,
            eyeClosedIcon,
        };
    },
    methods: {
        togglePasswordVisibility() {
            this.showPassword = !this.showPassword;
        },
        toggleConfirmPasswordVisibility() {
            this.showConfirmPassword = !this.showConfirmPassword;
        },
    },
};
</script>