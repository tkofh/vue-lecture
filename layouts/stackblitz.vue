<template>
  <StackBlitzEditor :project-id="props.projectId" :project-file="props.projectFile" />
</template>

<script setup lang="ts">
import StackBlitzEditor from '../components/StackBlitzEditor.vue'
const props = defineProps<{ projectId: string; projectFile: string }>()
</script>
