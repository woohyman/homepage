<template>
  <div class="project-wrapper">
    <ModernProjects />
  </div>
</template>

<script>
import ModernProjects from '@/components/modern/ModernProjects.vue'

export default {
  name: 'project',
  components: {
    ModernProjects
  }
}
</script>

<style scoped>
.project-wrapper {
  width: 100%;
  background: var(--gray-50);
}
</style>
