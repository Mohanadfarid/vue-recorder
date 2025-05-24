<script setup lang="ts">
import RecordedItemsList from '@/components/RecordedItemsList.vue';
import RecorderForm from '@/components/RecorderForm.vue';

</script>
<template>
  <div class="border flex flex-col w-full h-full p-6">
    <div class="grow">
      <RecordedItemsList class="h-full p-3 flex flex-col items-end" />
    </div>
    <div>
      <RecorderForm />
    </div>
  </div>
</template>

<style></style>
