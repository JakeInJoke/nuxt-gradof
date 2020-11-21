<template>
  <div class="flex">
    <Title :title="title" />
    <container-wo :plh="placeholder" :dataURL="tbody" :filtercol="thead" />
  </div>
</template>
<script>
import ContainerWO from '@/components/ContainerWO.vue'
var url = ''
export default {
  data() {
    return {
      title: 'Usuarios',
      placeholder: 'Buscar usuario...',
    }
  },
  components: {
    'container-wo': ContainerWO,
  },
  async asyncData({ $axios }) {
    const thead = await $axios.get('/cn.php?t=users')
    const tbody = await $axios.get('/get.php?t=users')
    return { thead: thead.data['data'], tbody: tbody.data['data'] }
  },
}
</script>
<style></style>
