<template>
  <div class="md:flex">
    <!-- Mobile Toggle Bar --START -->
    <button
      class="md:hidden p-2 text-white bg-primary fixed top-4 left-4 z-50 rounded"
      @click="sidebarOpen = !sidebarOpen"
    >
      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none"
           viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
              d="M4 6h16M4 12h16M4 18h16" />
      </svg>
    </button>

    <!-- Sidebar Bar --START -->
    <aside
       :class="[
    'fixed z-40 md:static top-0 left-0 h-screen w-64 bg-primary text-white p-4 transform transition-transform duration-300 flex flex-col',
    sidebarOpen ? 'translate-x-0' : '-translate-x-full md:translate-x-0'
  ]"
    >
      <!-- Brand Logo -->
      <div class="main-logo mb-2"><img
            :src="`../src/assets/images/main-logo.png`"
            alt="timeline icon image is displaying here in the left side"
            class="px-3 "
          /></div>

      <!-- Navigation Bar --START -->
      <nav class="nav-bar flex-1">
        <ul class="space-y-2">
          <li class="nav-bar__item">
            <a href="#" class="flex items-center gap-2 p-2">
              <HomeIcon /> Home
            </a>
          </li>
          <li class="nav-bar__item">
            <button @click="toggleDropdown" class="flex items-center justify-between w-full p-2">
              <span class="flex items-center gap-2">
                <TimerIcon /> View sessions
              </span>
              <ChevronIcon :open="dropdownOpen" />
            </button>
            <ul v-if="dropdownOpen" class="ml-6 mt-1 space-y-1">
          <li class="nav-bar__item">
            <a href="#" class="flex items-center gap-2 py-3 px-2">
              <FolderIcon /> All Sessions
            </a>
          </li>
          <li class="nav-bar__item">
            <a href="#" class="flex items-center gap-2 py-3 px-2">
              <RecentIcon /> Recent
            </a>
          </li>
          <li class="nav-bar__item">
            <a href="#" class="flex items-center gap-2 py-3 px-2">
              <ArchiveIcon /> Archived
            </a>
          </li>
        </ul>
          </li>
          <li class="nav-bar__item">
            <a href="#" class="flex items-center gap-2 p-2">
              <img
            :src="`/src/assets/images/user-circle.png`"
            alt=""
            class="w-6 h-6"
          /> Patient records
            </a>
          </li>
          <li class="nav-bar__item">
            <a href="#" class="flex items-center gap-2 p-2">
              <MediaIcon /> Media
            </a>
          </li>
          <li class="nav-bar__item">
            <a href="#" class="flex items-center gap-2 p-2">
              <img
            :src="`/src/assets/images/virtual-laptop.png`"
            alt=""
            class="w-6 h-6"
          /> Virtual consultation
            </a>
          </li>
          <li class="nav-bar__item">
            <a href="#" class="flex items-center gap-2 p-2">
              <BarChartIcon /> Statistics
            </a>
          </li>
        </ul>
      </nav>


<div class="mt-auto nav-bar-bottom-btn">
  <button
    @click="profileOpen = !profileOpen"
    class="w-full flex items-start gap-3 px-2 py-2"
  >
    <!-- Profile Circle Dropdown --START-->
    <div class="nav-bar-bottom-btn__icon  flex items-center justify-center">
      RL
    </div>

    <div class="flex-1">
      <div class="nav-bar-bottom-btn__name">Robert Lindsey</div>
      <div class="nav-bar-bottom-btn__email truncate w-full">robertlindsey@sho...</div>
    </div>
    <ChevronIcon :open="profileOpen" />
  </button>

  <ul
    v-if="profileOpen"
    class="dd-btn-menu bottom-full mb-1 w-full text-black text-sm rounded shadow z-50"
  >
    <li class="dd-btn-menu__item"><a href="#" class="flex items-center gap-2 p-2"><ProfileIcon/>My Profile</a></li>
    <li class="dd-btn-menu__item"><a href="#" class="flex items-center gap-2 p-2"><SettingsIcon/>Settings</a></li>
    <li class="dd-btn-menu__item"><a href="#" class="flex items-center gap-2 p-2"><LogoutIcon/>Logout</a></li>
  </ul>
</div>

    </aside>
  </div>
</template>

<script setup>
import { ref, h } from 'vue'
import {
  HomeIcon,
  FolderIcon,
  RecentIcon,
  ArchiveIcon,
  TimerIcon,
  MediaIcon,
  BarChartIcon,
  ChevronIcon,
  ProfileIcon,
  SettingsIcon,
  LogoutIcon
} from '@/components/icons'

const dropdownOpen = ref(false)
const profileOpen = ref(false)
const sidebarOpen = ref(false)
const toggleDropdown = () => dropdownOpen.value = !dropdownOpen.value
</script>

<style scoped>
/* Optional: prevent body scroll on mobile when sidebar open */
body {
  overflow-x: hidden;
}
</style>
