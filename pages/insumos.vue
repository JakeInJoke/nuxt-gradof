<template>
  <div class="flex">
    <Title :title="title" />
    <container-wo :plh="placeholder" :dataURL="tbody" :filtercol="thead" />
  </div>
</template>
<script>
import ContainerWO from '@/components/ContainerWO.vue'
export default {
  data() {
    return {
      title: 'Insumos',
      placeholder: 'Buscar insumo...',
    }
  },
  components: {
    'container-wo': ContainerWO,
  },
  async asyncData({ $axios }) {
    const thead = await $axios.get('/cn.php?t=view_insumos')
    const tbody = await $axios.get('/get.php?t=view_insumos')
    return { thead: thead.data['data'], tbody: tbody.data['data'] }
  },
}
</script>
<style></style>
