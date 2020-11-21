<template>
  <div class="flex">
    <Title :title="title" />
    <container-wo :plh="placeholder" />
  </div>
</template>
<script>
import ContainerWO from '@/components/ContainerWO.vue'
export default {
  data() {
    return {
      title: 'Historial',
      placeholder: 'Buscar en el historial...',
    }
  },
  components: {
    'container-wo': ContainerWO,
  },
}
</script>
<style></style>
