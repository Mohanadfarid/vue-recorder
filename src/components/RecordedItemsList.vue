<script setup lang="ts">

import RecordedItem from "@/components/RecordedItem.vue";
type RecordingModule = { default: string };


const recordings = import.meta.glob("../assets/audio/*.mp3", { eager: true }) as Record<string,RecordingModule>;
const recordingsPathes = Object.keys(recordings);

</script>
<template>
  <div class="bg-[url('../assets/background.jpg')]">
    <RecordedItem
      v-for="path in recordingsPathes"
      :key="path"
      :audio-url="recordings[path].default"
    />
  </div>
</template>
<style></style>
