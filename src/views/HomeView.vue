<script setup>
import Hero from "@/components/Hero.vue";
import HomeCards from "@/components/HomeCards.vue";
import JobListings from "@/components/JobListings.vue";
</script>

<template>
    <Hero title='Become a Specialist' />
    <HomeCards />
    <JobListings :limit="6" :showButton="true" />
</template>