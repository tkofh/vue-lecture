<template>
  <div class="stackblitz-editor w-full h-full flex items-stretch">
    <div :id="`editor-${props.projectId}`"></div>
  </div>
</template>

<script setup lang="ts">
import sdk from '@stackblitz/sdk'
import { onMounted } from 'vue'
const props = defineProps<{ projectId: string; projectFile: string }>()
onMounted(() => {
  sdk.embedProjectId(
    `editor-${props.projectId}`,
    props.projectId,
    {
      forceEmbedLayout: true,
      openFile: props.projectFile,
      hideNavigation: true,
    }
  );
})
</script>

<style>
.stackblitz-editor iframe {
  height: 100%;
}
</style>
