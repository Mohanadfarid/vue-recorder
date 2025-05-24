<script setup lang="ts">
import { computed, onMounted } from "vue";
import WaveSurfer from "wavesurfer.js";

const props = defineProps<{
  audioUrl: string;
}>();

const audioName = computed(() => {
  const audioUrlSegments = props.audioUrl.split("/");
  const auidoNameWithExtention = audioUrlSegments[audioUrlSegments.length - 1];
  const audioName = auidoNameWithExtention.split(".")[0];
  return audioName;
});

onMounted(() => {
  const wavesurfer = WaveSurfer.create({
    container: `#${audioName.value}`,
    waveColor: "#B0CEAE",
    progressColor: "#728977",
    url: props.audioUrl,
    barGap: 2,
    barWidth: 3,
    barHeight: 1,
    barRadius: 1,
    height: 50,
    cursorWidth: 4,
    cursorColor: "#4FC3F7",
  });

  wavesurfer.on("click", () => {
    wavesurfer.play();
  });

  wavesurfer.on('finish',()=>{
    wavesurfer.seekTo(0)
  })
});
</script>
<template>
  <div class="shadow rounded-2xl p-3 m-1 w-[350px] bg-[#d9fdd3] flex items-center">
    <img
      class="rounded-full me-3"
      src="https://loremflickr.com/200/200?random=1"
      width="60"
      height="60"
      alt=" just a random avatar pic "
    />

    <div class="grow" :id="audioName"></div>
  </div>
</template>
<style>

</style>
