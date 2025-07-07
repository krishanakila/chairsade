<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import Sidebar from '@/components/Sidebar.vue'
import Notes from '@/components/Notes.vue'
import Timeline from '@/components/Timeline.vue'

const showTimeline = ref(true)
const isDesktop = ref(window.innerWidth >= 768)

const updateDeviceSize = () => {
  isDesktop.value = window.innerWidth >= 768
}

onMounted(() => {
  window.addEventListener('resize', updateDeviceSize)
})

onBeforeUnmount(() => {
  window.removeEventListener('resize', updateDeviceSize)
})
</script>


<template>
  <div class="relative h-screen overflow-auto">
    <!-- Toggle Timeline Button -->
    <button
      v-if="!isMobile"
      class="toggle-btn absolute top-4 right-4 z-50 bg-white border rounded-full shadow p-2 hover:bg-gray-50 transition-all duration-300"
      @click="showTimeline = !showTimeline"
      aria-label="Toggle Timeline Panel"
    >
      <svg
        class="w-5 h-5 transition-transform duration-500"
        :class="{ 'rotate-180': !showTimeline }"
        fill="none"
        stroke="currentColor"
        viewBox="0 0 24 24"
      >
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
      </svg>
    </button>

    <!-- Grid Layout -->
    <div
  class="main-wrapper grid h-full transition-all duration-700 ease-in-out overflow-y-auto"
  :class="[
    showTimeline && isDesktop ? 'grid-cols-[auto_1fr_352px]' : isDesktop ? 'grid-cols-[auto_1fr_0px]' : 'grid-cols-1'
  ]"
>
      <!-- Sidebar -->
      <Sidebar />

      <!-- Notes Panel -->
      <div
    class="transition-all duration-700 ease-in-out"
    :class="isDesktop ? 'overflow-y-auto' : 'overflow-visible'"
  >
        <Notes />
      </div>

      <!-- Timeline Panel -->
       <div
    class="transition-all duration-700 ease-in-out"
    :class="isDesktop ? 'overflow-y-auto' : 'overflow-visible'"
    :aria-hidden="!showTimeline && isDesktop"
  >
        <Timeline />
      </div>
    </div>
  </div>
</template>

<style scoped>
.rotate-180 {
  transform: rotate(180deg);
}
</style>
