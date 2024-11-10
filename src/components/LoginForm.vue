<template>
    <form @submit.prevent="handleLogin">
        <div class="bg-pure-white shadow-lg rounded-lg p-5 mt-6">
            <div class="bg-white flex items-center rounded p-2">
                <img src="../assets/person.svg" alt="" class="w-8 h-8" />
                <input required type="text" placeholder="Email / No. HP" v-model="email"
                    class="text-gray font-semibold ml-2 w-full outline-none bg-white" />
            </div>
            <div class="mt-4 bg-white flex items-center rounded relative p-2">
                <img src="../assets/lock.svg" alt="" class="w-8 h-8" />
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
</template>

<script>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import eyeOpenIcon from '../assets/eye-open.svg';
import eyeClosedIcon from '../assets/eye-closed.svg';

export default {
    name: 'LoginForm',
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