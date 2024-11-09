<template>
  <nav class="w-full md:hidden bg-secondary text-white p-2">
    <ul class="flex justify-between items-center space-x-4 h-14">
      <li v-for="item in navItems" :key="item.path">
        <router-link :to="item.path" class="py-3 px-4 rounded flex items-center"
          :class="{ 'bg-white text-primary font-bold': $route.path === item.path }">
          <img :src="$route.path === item.path ? item.iconFilled : item.icon" :alt="item.name" class="mr-2" />
          <span v-if="$route.path === item.path">{{ item.name }}</span>
        </router-link>
      </li>
    </ul>
  </nav>
</template>

<script>
import HomeFilledIcon from '../assets/home-filled.svg';
import HomeIcon from '../assets/home.svg';
import HistoryFilledIcon from '../assets/history-filled.svg';
import HistoryIcon from '../assets/history.svg';
import ChatFilledIcon from '../assets/chat-filled.svg';
import ChatIcon from '../assets/chat.svg';
import AccountFilledIcon from '../assets/account-filled.svg';
import AccountIcon from '../assets/account.svg';

export default {
  name: 'Navbar',
  data() {
    return {
      navItems: [
        {
          name: 'Home',
          path: '/home',
          icon: HomeIcon,
          iconFilled: HomeFilledIcon,
        },
        {
          name: 'Riwayat',
          path: '/riwayat',
          icon: HistoryIcon,
          iconFilled: HistoryFilledIcon,
        },
        {
          name: 'Pesan',
          path: '/pesan',
          icon: ChatIcon,
          iconFilled: ChatFilledIcon,
        },
        {
          name: 'Akun',
          path: '/akun',
          icon: AccountIcon,
          iconFilled: AccountFilledIcon,
        },
      ],
    };
  },
};
</script>
