<template>
    <div class="flex flex-col items-center">
        <img src="../assets/logo-big.svg" alt="Logo Harapan Klinik" class="m-auto mb-8 lg:mb-12" />
        <InformationCard class="hidden md:flex flex-col" />
    </div>
</template>

<script>
import InformationCard from './InformationCard.vue';

export default {
    name: 'HeroSection',
    components: {
        InformationCard
    }
};
</script>