<template>
  <div class="slidev-layout iframe-right">
    <div class="container">
      <div class="content">
        <slot/>
      </div>
      <iframe
          id="frame" class="w-full h-full"
          :src="url"
          :style="scale ? { transform: `scale(${scale})`, transformOrigin: 'top left' } : {}"
      />
    </div>
  </div>
  <Footer :event-name="eventName" :eventDate="eventDate" :show-dynatrace-logo="showDynatraceLogo" :showSlideNumber="showSlideNumber"/>
</template>

<script setup>
import Footer from "../components/Footer.vue";
import {defineProps} from 'vue';

defineProps({
  url: {
    type: String,
  },
  scale: {
    type: String,
  },
  eventName: {
    type: String,
  },
  eventDate: {
    type: String
  },
  showDynatraceLogo: {
    type: Boolean,
  },
  showSlideNumber: {
    type: Boolean
  }
})
</script>

<style scoped>
.container {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: row;
  padding: 0;
  margin: 0;
}

#frame {
  width: 50%;
}

.content {
  padding: 2.5rem 3.5rem;
  flex-grow: 1;
}
</style>