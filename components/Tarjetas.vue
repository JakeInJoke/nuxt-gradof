<template>
  <div>
    <h1 v-for="(option, i) in options" :key="i">
      Esta es la opcion {{ (i = 1) }} : {{ option.text }}
    </h1>
  </div>
</template>
<script>
export default {
  data() {
    return {
      options: [
        { text: 'Codigo', value: 'Codigo' },
        { text: 'Nombre', value: 'Nombre' },
        { text: 'Apellido', value: 'Apellido' },
        { text: 'Usuario', value: 'Usuario' },
        { text: 'Correo', value: 'Correo' },
        { text: 'Area', value: 'Area' },
      ],
    }
  },
}
</script>
<style lang="sass"></style>
