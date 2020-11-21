<template>
  <div class="title-container">
    <h1 id="title">{{ title }}</h1>
  </div>
</template>
<script>
export default {
  props: {
    title: {
      type: String,
      default: 'Titulo de la vista',
    },
  },
}
</script>
<style lang="sass">
.title-container
    height: 70px
    padding-left: 50px
#title
    margin: 0
    height: 70px
    font-family: $fontArchivoNarrow
    //color: $shadowTitleViewPred
    color: $backgroundSidebarPred
    font-size: 50px
</style>
