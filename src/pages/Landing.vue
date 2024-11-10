<template>
  <div class="grid place-items-center min-h-screen">
    <!-- Tampilan Mobile -->
    <div class="relative w-full flex flex-col md:hidden">
      <div class="absolute top-0 w-full h-96 bg-primary rounded-b-xl z-10"></div>
      <div class="absolute top-0 w-full h-full bg-white z-0"></div>
      <div class="relative z-20 pt-6">
        <HeroSection />
        <div class="m-4 mt-10">
          <AuthCard />
        </div>
        <div class="px-4">
          <InformationCard />
        </div>
      </div>
    </div>

    <!-- Tampilan Desktop -->
    <div class="hidden md:flex w-full h-full lg:h-fit lg:w-10/12 bg-primary lg:rounded-lg items-center">
      <div class="flex-1 p-8">
        <HeroSection />
      </div>
      <div class="flex-1 p-8">
        <AuthCard />
      </div>
    </div>
  </div>
</template>

<script>
import HeroSection from '../components/HeroSection.vue';
import AuthCard from '../components/AuthCard.vue';
import InformationCard from '../components/InformationCard.vue';

export default {
  name: 'Landing',
  components: {
    HeroSection,
    AuthCard,
    InformationCard
  }
};
</script>
