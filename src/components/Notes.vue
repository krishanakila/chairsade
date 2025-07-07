<script setup>


</script>

<template>
  <section class="relative flex flex-col h-screen border-r border-gray-200">
    <!-- Header Section -->
    <div class="header sticky top-0 z-10 shadow-sm">     
      <Header/>

      <!-- Sub Header Tabs --START-->
      <div class="header-secondary flex flex-col gap-3 sm:flex-row sm:items-center sm:justify-between px-4" role="tablist" aria-label="Session tabs">
        <!-- Tabs -->
        <div class="header-secondary__tab flex gap-4">
          <button
            id="tab-notes"
            role="tab"
            :aria-selected="activeTab === 'notes'"
            :aria-controls="'panel-notes'"
            :class="activeTab === 'notes' ? '' : ''"
            @click="activeTab = 'notes'"
          >
            Notes
          </button>
          <button
            id="tab-bundle"
            role="tab"
            :aria-selected="activeTab === 'bundle'"
            :aria-controls="'panel-bundle'"
            :class="activeTab === 'bundle' ? '' : ''"
            @click="activeTab = 'bundle'"
          >
            Bundles
          </button>
        </div>

        <!-- Edit Session Button--START -->
        <button class="primary-btn mb-4 md:mb-0">
          <EditIcon class="primary-btn__icon mr-2"/> Edit session
        </button>
      </div>
    </div>

    <!-- Scrollable Content -->
    <div class="panel-notes flex-1 overflow-y-auto pb-2">
      <!-- Notes Panel -->
      <div
        v-if="activeTab === 'notes'"
        id="panel-notes"
        role="tabpanel"
        aria-labelledby="tab-notes"
        class="space-y-8"
      >
        <!-- Panel notes header section --START-->
        <div class="panel-notes__header flex flex-wrap items-center gap-2 justify-between">
          <button class="primary-btn primary-btn--mini" aria-label="Select Template A">
            <NewFolderIcon class="mr-2"/> Template A
          </button>
          <div class="flex gap-2">
            <button class="squre-btn squre-btn--mini p-2" aria-label="Search"><ButtonWithIcons/></button>
            <button class="squre-btn squre-btn--mini p-2" aria-label="Download"><DownloadIcon/></button>
          </div>
        </div>

        <!-- Panel notes row 1 section --START-->
        <div class="panel-notes__row-1">
          <p class="typo-32">Notes</p>
          <p class="typo-12">Last updated today 09:15 AM</p>
         </div>

         <hr style="margin-top: 15px;"/>

        <!-- Panel notes row 2 section --START-->
        <div class="panel-notes__row-2 space-y-6 text-sm">
          <div class="panel-notes__item">
            <p class="typo-14">Dentist</p>
            <p class="typo-14--normal">Dr John Smith</p>
          </div>


          <div class="panel-notes__item">
          <label for="nurse-input" class="block typo-14 mb-1">Nurse</label>
          <input
            id="nurse-input"
            type="text"
            placeholder="Type here"
            class=""
          />
         </div>


          <div class="panel-notes__item">
            <p class="typo-14 mb-2">When did the fracture occur?</p>
            <div class="flex flex-wrap gap-2" role="group" aria-label="Fracture occurrence options">
              <span class="chip chip--primary">Today</span>
              <span class="chip chip--primary">Yesterday</span>
              <span class="chip chip--primary">Several days ago</span>
              <span class="chip chip--primary">Over a week ago</span>
              <span class="chip chip--primary">N/A</span>
            </div>
          </div>

          <div class="panel-notes__item">
          <label for="location-broken" class="block typo-14 mb-1">Location of broken tooth</label>
          <input
            id="nurse-input"
            type="text"
            value="Broken tooth lorem"
            placeholder=""
            class="typo-14--normal"
          />
          </div>

          <div class="panel-notes__item">
          <label for="location-broken" class="block typo-14 mb-1">Reason for attendance</label>
          <input
            id="nurse-input"
            type="text"
            value="Broken tooth lorem"
            placeholder=""
            class="typo-14--normal"
          />
          </div>

          <div class="panel-notes__item">
          <label for="location-broken" class="block typo-14 mb-1">When did the fracture occur?</label>
          <input
            id="nurse-input"
            type="text"
            value="Broken tooth"
            placeholder=""
            class="typo-14--normal"
          />
          </div>

          <div class="panel-notes__item">
          <label for="location-broken" class="block typo-14 mb-1">How did it happen?</label>
          <input
            id="nurse-input"
            type="text"
            value="Broken tooth"
            placeholder=""
            class="typo-14--normal"
          />
          </div>
        </div>
      </div>

      <!-- Bundle Panel -->
      <div
        v-else-if="activeTab === 'bundle'"
        id="panel-bundle"
        role="tabpanel"
        aria-labelledby="tab-bundle"
        class="space-y-4"
      >
      
        <div class="panel-bundle flex-1 overflow-y-auto bg-white m-4 " style="height:500px">




        </div>







       
       
      </div>
    </div>
  </section>
</template>

<script setup>
import Header from '@/components/Header.vue'
import { ref } from 'vue'
const activeTab = ref('notes')


import {
  EditIcon,
  NewFolderIcon,
  ButtonWithIcons,
  DownloadIcon
} from '@/components/icons'


</script>

<style scoped>
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