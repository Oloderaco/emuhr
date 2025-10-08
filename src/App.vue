<script setup>
import './styles/main.css'
import MainLayout from './layouts/MainLayout.vue';
import StatsSection from './sections/StatsSection.vue';
import FeaturesSection from './sections/FeaturesSection.vue';
import PricingSection from './sections/PricingSection.vue';
import CTASection from './sections/CTASection.vue';

</script>

<template>
<MainLayout>
  <StatsSection/>
  <FeaturesSection/>
  <PricingSection/>
  <CTASection/>
</MainLayout>
</template>

<style scoped></style>
