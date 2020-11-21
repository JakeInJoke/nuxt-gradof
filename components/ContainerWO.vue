<template>
  <div class="container-view">
    <div class="container-options">
      <div class="search-bar">
        <vs-input
          color="rgb(59,222,200)"
          v-model="search"
          :placeholder="plh"
          spellcheck="false"
        />
      </div>
      <div class="search-dropdown">
        <vs-input
          color="#3d688a"
          type="date"
          v-model="dateFrom"
          label="Desde"
        />
        <vs-input color="#3d688a" type="date" v-model="dateTo" label="Hasta" />
      </div>
    </div>
    <TableAType
      :filter="filter"
      :dataJSON="dataAPI"
      :search="search"
      :allCheck="allCheck"
      :selected="selected"
    />
  </div>
</template>
<script>
import moment from 'moment'
export default {
  props: {
    search: {
      type: String,
      default: '',
    },
    filtercol: {
      type: Array,
    },
    dataURL: {
      type: Array,
    },
    plh: {
      type: String,
      default: 'Buscar...',
    },
    label: {
      type: String,
      default: 'Opciones',
    },
  },
  methods: {},
  data() {
    return {
      dateFrom: moment().format('YYYY-MM-DD'),
      dateTo: moment().format('YYYY-MM-DD'),
      allCheck: false,
      filter: this.filtercol,
      selected: [],
      dataAPI: this.dataURL,
    }
  },
}
</script>
<style lang="sass">
.container-view
    display: flex
    flex-wrap: wrap
    margin-top: 25px
    background-color: $backgroundDeep
    height: calc( 100% - 95px )
    width: 100%
    box-sizing: border-box
    border-top: 1px solid $borderColorPred
.container-options
    width: 100%
    height: 70px
    background-color: $backgroundDeep1
    border-bottom: 1px solid $borderColorPred
    display: flex
    align-items: center
    padding-left: 50px
    padding-right: 50px
    .search-bar
      display: flex
      flex-wrap: wrap
      height: 40px
      width: 25%
      min-width: 255px
      .vs-input-parent
        height: 40px
        width: 200px
        width: 100%
        .vs-input-content
          min-height: 40px
          .vs-input__label
            font-size: 16px
          .vs-input,.vs-input__label
              font-family: $fontArchivoNarrow
          .vs-input
              //background-color: white
              width: 100%
      button
        border: none
        height: 40px
        width: 40px
        margin-left: 15px
        border-radius: 12px
        background-color: $backgroundSidebarPred
        color: $fontColorSidebarHoverPred
        cursor: pointer
        outline: none
        box-sizing: border-box
        box-shadow: 0px 3px 1px -2px rgba(0, 0, 0, 0.2), 0px 2px 2px 0px rgba(0, 0, 0, 0.14), 0px 1px 5px 0px rgba(0, 0, 0, 0.12)
        &:hover
          background-color: $linkBackgroundSidebarActivePred

.search-dropdown
  margin-left: 30px
  font-family: $fontArchivoNarrow
  display: flex
  align-items: center
  //justify-content: center
  height: 40px
  width: 75%
  .vs-input-content
    margin-left: 20px
    .vs-input
      width: 150px
    .vs-input__label
      font-size: 13px
      height: 30px
  .vs-select-content
    width: 100%
    max-width: 100%
    max-width: calc(100% - 255px)
  /*.vs-icon-arrow
    &::after,&::before
      background: $fontColorSidebarHoverPred
  .vs-select__chips
    &:hover
      transform: none
      -webkit-transform: none
/*  .vs-select__chips,.vs-select.activeOptions .vs-select__chips
    background-color: $backgroundSidebarPred
    color: $fontColorSidebarHoverPred
  .vs-select__chips__input
    font-family: $fontArchivoNarrow
    color: $fontColorSidebarHoverPred
    &::placeholder
      color: $fontColorSidebarHoverPred
      opacity: 0.8
    &:-ms-input-placeholder
      color: $fontColorSidebarHoverPred
      opacity: 0.8
    &::-ms-input-placeholder
      color: $fontColorSidebarHoverPred
      opacity: 0.8
.vs-select__option.isMultiple .vs-checkbox-content .vs-checkbox-label
  font-family: $fontArchivoNarrow
  //color: $fontColorSidebarHoverPred
/*.vs-select__options
  background-color: $backgroundSidebarPred
.vs-select__options__content__not-data
  font-family: $fontArchivoNarrow
  //color: $fontColorSidebarHoverPred
/*.vs-select__option.isHover.isMultiple,.vs-select__option.isMultiple.isHover,.vs-select__option.isHover
  background-color: transparent !important
.table-container
  width: 100%
  height: calc(100% - 70px)
  position: relative
  font-family: $fontOpenSans
  .table-view
    position: absolute
    top: 0
    left: 0
    bottom: 0
    right: 0
    background-color: white
    border-radius: 14px
    margin: 70px 70px 70px 70px
    .vs-table__tr
      background-color: white
.vs-table-content,.vs-icon-check
  --vs-color: var(--vs-deepsea)
.vs-checkbox-content
  --vs-color: var(--vs-boole)
</style>
