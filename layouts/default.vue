<template>
  <div id="app">
    <div id="sidebar">
      <div id="sidebar-top">
        <nuxt-link
          v-for="(item, index) in routesT"
          :key="index"
          :to="item.route"
          :data-tippy-content="item.tooltip"
        >
          <span>
            <font-awesome-icon :icon="['fas', item.icon]" />
          </span>
        </nuxt-link>
      </div>
      <div id="sidebar-bottom">
        <nuxt-link
          v-for="(item, index) in routesB"
          :key="index"
          :to="item.route"
          :data-tippy-content="item.tooltip"
        >
          <span>
            <font-awesome-icon :icon="['fas', item.icon]" />
          </span>
        </nuxt-link>
      </div>
    </div>
    <div id="view">
      <Nuxt />
    </div>
  </div>
</template>
<script>
import tippy from 'tippy.js'
import('tippy.js/dist/tippy.css')
export default {
  data() {
    return {
      routesT: [
        { icon: 'chart-line', route: '/', tooltip: 'Resumen' },
        { icon: 'shopping-cart', route: '/productos', tooltip: 'Productos' },
        { icon: 'box', route: '/insumos', tooltip: 'Insumos' },
        { icon: 'users', route: '/usuarios', tooltip: 'Usuarios' },
        { icon: 'file-alt', route: '/reportes', tooltip: 'Reportes' },
        { icon: 'history', route: '/historial', tooltip: 'Historial' },
        { icon: 'info-circle', route: '/nosotros', tooltip: 'Nosotros' },
      ],
      routesB: [
        { icon: 'user-circle', route: '/perfil', tooltip: 'Perfil' },
        { icon: 'cog', route: '/configuracion', tooltip: 'Configuracion' },
        { icon: 'sign-out-alt', route: '/out', tooltip: 'Cerrar Sesion' },
      ],
    }
  },
  beforeCreate() {
    if (process.client) {
      tippy('a', {
        animation: 'scale',
        arrow: true,
        placement: 'right',
        animation: 'fade',
        theme: 'gradof',
      })
    }
  },
}
</script>
<style lang="sass">
html
  overflow: hidden
html,body,#__nuxt,#__layout,#app
  height: 100%
  width: 100%
  margin: 0
  padding: 0
#app
  display: flex
.nuxt-link-exact-active
  color: $fontColorSidebarActivePred !important
  background-color: $linkBackgroundSidebarActivePred
.flex
  display: flex
  flex-wrap: wrap
  height: 100%
#sidebar
  position: relative
  width: 50px
  z-index: 1
  background: $backgroundSidebarPred
  filter: drop-shadow(3px 0px 3px $shadowSidebarPred)
  #sidebar-bottom
    position: absolute
    bottom: 0
  #sidebar-bottom,#sidebar-top,#sidebar-search
    width: 100%
    display: flex
    flex-wrap: wrap
    a
      display: flex
      align-items: center
      justify-content: center
      color: $fontColorSidebarPred
      height: 50px
      width: 100%
      font-size: 25px
      &:hover
        color: $fontColorSidebarHoverPred
#view
  background-color: $backgroundViewPred
  width: 100%
  //padding-left: 50px
  //padding-right: 50px
  padding-top: 25px
  //padding-bottom: 25px

.tippy-box[data-theme~='gradof']
    background-color: $fontColorSidebarHoverPred
    font-family: $defaultFont
    height: 40px
    display: flex
    align-items: center
    justify-content: center
    font-weight: 700
    font-size: 15px
    padding: 0 10px 0 10px
    color: $backgroundSidebarPred

.tippy-box[data-theme~='gradof'][data-placement^='top'] > .tippy-arrow::before
    border-top-color: $fontColorSidebarHoverPred

.tippy-box[data-theme~='gradof'][data-placement^='bottom'] > .tippy-arrow::before
    border-bottom-color: $fontColorSidebarHoverPred

.tippy-box[data-theme~='gradof'][data-placement^='left'] > .tippy-arrow::before
    border-left-color: $fontColorSidebarHoverPred

.tippy-box[data-theme~='gradof'][data-placement^='right'] > .tippy-arrow::before
    border-right-color: $fontColorSidebarHoverPred
</style>
