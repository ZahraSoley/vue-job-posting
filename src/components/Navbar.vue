<script setup>
// import logo from "@/assets/logo.png";
import { RouterLink, useRoute } from 'vue-router';

const links = [
  {
    title: 'Home',
    path: '/'
  },
  {
    title: 'Jobs',
    path: '/jobs'
  },
  {
    title: 'Add Job',
    path: '/jobs/add'
  }
]

const isActiveLink = (routePath) => {
  const route = useRoute()
  return routePath === route.path
}
</script>

<template>
  <nav class="bg-green-700 border-b border-green-500">
    <div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
      <div class="flex h-20 items-center justify-between">
        <div class="flex flex-1 items-center justify-center md:items-stretch md:justify-start">
          <!-- Logo -->
          <RouterLink class="flex shrink-0 items-center mr-4" href="/">
            <!-- <img class="h-10 w-auto" :src="logo" alt="a suitcase with wings as the logo" /> -->
            <span class="hidden md:block text-white text-2xl font-bold ml-2">Vue Jobs</span>
          </RouterLink>
          <div class="md:ml-auto">
            <div class="flex space-x-2">
              <RouterLink v-for="link in links" :to="link.path"
                :class="['text-white', 'rounded-md', 'px-3', 'py-2', isActiveLink(link.path) ? 'bg-green-900' : 'hover:bg-gray-900 hover:text-white']">
                {{ link.title }}
              </RouterLink>
            </div>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>
