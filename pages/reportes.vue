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
      title: 'Reportes',
      placeholder: 'Buscar reporte...',
    }
  },
  components: {
    'container-wo': ContainerWO,
  },
}
</script>
<style></style>
