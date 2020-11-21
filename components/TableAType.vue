<template>
  <div class="table-container">
    <div class="table-view">
      <div class="center">
        <vs-table v-model="selected">
          <template #thead>
            <vs-tr>
              <vs-th>
                <vs-checkbox
                  :indeterminate="selected.length == dataJSON.length"
                  v-model="allCheck"
                  @change="selected = $vs.checkAll(selected, dataJSON)"
                />
              </vs-th>
              <vs-th v-for="(item, i) in filter" :key="i">
                {{ item.columna }}
              </vs-th>
            </vs-tr>
          </template>
          <template #tbody>
            <vs-tr
              :key="i"
              v-for="(tr, i) in $vs.getSearch(dataJSON, search)"
              :data="tr"
              :is-selected="!!selected.includes(tr)"
            >
              <vs-td checkbox>
                <vs-checkbox :val="tr" v-model="selected" />
              </vs-td>
              <vs-td v-for="(fill, o) in tr" :key="o">
                {{ fill }}
              </vs-td>
            </vs-tr>
          </template>
        </vs-table>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    colx: {
      type: Array,
    },
    filter: {
      type: Array,
    },
    dataJSON: {
      type: Array,
    },
    search: {
      type: String,
    },
    allCheck: {
      type: Boolean,
    },
    selected: {
      type: Array,
    },
    table: {
      type: String,
    },
  },
  data() {
    return {}
  },
}
</script>
<style lang="sass">
.center
    max-height: 100%
    overflow: auto
</style>
