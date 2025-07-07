<template>
  <aside class="timeline flex flex-col h-screen mx-4 md:mx-0">
  <div class="timeline__header">
    <p class="timeline__header-title flex items-center justify-center mb-4">Timeline</p>
   </div> 
    <div class="timeline__inner-wrapper flex-1 overflow-y-auto overflow-x-hidden space-y-6 pr-2">
      <div
        v-for="(event, index) in timelineEvents"
        :key="index"
        class="timeline__item relative flex items-start gap-3 px-4"
      >
        <div
          class="w-10 h-10 flex-shrink-0 flex items-center justify-center">
          <img
            :src="`/src/assets/images/${event.icon}`"
            alt="timeline icon image is displaying here in the left side"
            class="w-10 h-10"
          />
        </div>
        <div>
          <p class="timeline__time">{{ event.time }}</p>
          <p class="timeline__title">{{ event.title }}</p>
          <p v-if="event.description" class="timeline__des whitespace-pre-line">
            {{ event.description }}
          </p>
          <p v-if="event.email" class="timeline__email">
            {{ event.email }}
          </p>
        </div>
      </div>
    <div class="timeline__seperator px-4">
    <hr class="timeline__seperator-line" />
    <p class="timeline__seperator-text my-5">Appointment ends • 1 July, 10:00 AM</p>
    </div>


    <div
        v-for="(event, index) in additionalEvents"
        :key="index"
        class="timeline__item relative flex items-start gap-3 px-4"
      >
        <div
          class="w-10 h-10 flex-shrink-0 flex items-center justify-center"
          :class="event.bgColor"
        >
          <img
            :src="`/src/assets/images/${event.icon}`"
            alt=""
            class="w-10 h-10 object-contain"
          />
        </div>
        <div>
          <p class="timeline__time">{{ event.time }}</p>
          <p class="timeline__title">{{ event.title }}</p>
          <p v-if="event.description" class="timeline__des whitespace-pre-line">
            {{ event.description }}
          </p>
          <p v-if="event.email" class="timeline__email">
            {{ event.email }}
          </p>
        </div>
      </div>

<div class="timeline__seperator px-4 pb-6">
<span class="timeline__seperator-text">Appointment begins • 1 July, 09:45 AM</span>
</div>
    </div>
  </aside>
</template>


<script setup>
import { timelineEvents, additionalEvents } from '@/data/timelineData.js'
</script>

<style scoped>
.custom-scrollbar::-webkit-scrollbar {
  width: 2px;
}
.custom-scrollbar::-webkit-scrollbar-thumb {
  background-color: rgba(0, 0, 0, 0.1);
  border-radius: 6px;
}


/* Apply to any scrollable element or body */
::-webkit-scrollbar {
  width: 2px; /* Reduce width */
}

::-webkit-scrollbar-track {
  background: #f1f1f1;
}

::-webkit-scrollbar-thumb {
  background: #888;
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: #555;
}

</style>
