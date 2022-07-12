<template>
  <div>
    <el-checkbox
      v-for="(item, index) in list"
      :key="item.value"
      :value="checkedList[index] && ((checkedList[index].area.length === item.area.length) || (checkedList[index].ring.length === item.ring.length))"
      :indeterminate="checkedList[index] && ((checkedList[index].area.length > 0 && checkedList[index].area.length < item.area.length) || (checkedList[index].ring.length > 0 && checkedList[index].ring.length < item.ring.length))"
      @change="(e) => checkAll(e, item)"
    >
      {{ item.label }}
      <el-button @click="() => changeRegion(index)">
        切换地区
      </el-button>
    </el-checkbox>
    <Tab
      ref="tab"
      :data="areaData"
      :checked-data="checkedData"
      @checked="handleChecked"
    />
    {{ checkedList }}
  </div>
</template>
<script>
import { list } from './data'
import Tab from './Tab.vue'

export default {

  components: {
    Tab
  },

  mixins: [],
  props: {

  },

  data () {
    return {
      list,
      // areaData: [],
      checkedList: {},
      checkedData: {
        area: [],
        ring: []
      },
      regionIndex: 0
    }
  },

  computed: {
    areaData () {
      return this.list[this.regionIndex]
    }
  },

  watch: {

  },

  created () {

  },

  mounted () {
    this.checkedList = this.list.reduce((acc, cur, index) => {
      acc[index] = {
        area: [],
        ring: []
      }
      return acc
    }, {})
  },

  methods: {
    changeRegion (index) {
      this.regionIndex = index
      this.checkedData = this.checkedList[this.regionIndex]
    },
    handleChecked ({ event, item, type }) {
      let checkedItem = this.checkedList[this.regionIndex]

      Object.keys(this.checkedList).forEach(region => {
        Object.keys(checkedItem).forEach(key => {
          if (key !== type) {
            this.checkedList[region][key] = []
          }
        })
      })
      if (event) {
        if (checkedItem) {
          checkedItem[type].push(item.value)
        } else {
          checkedItem = {
            area: [],
            ring: []
          }
          checkedItem[type].push(item.value)
        }
      } else {
        // splice 这个应该可以封装一下，删除数组元素很常用
        checkedItem[type].splice(checkedItem[type].indexOf(item.value), 1)
      }
      this.checkedData = checkedItem
    },
    checkAll (e, item) {
      const checkedItem = this.checkedList[this.regionIndex]
      const type = this.$refs.tab.type
      if (e) {
        checkedItem[type] = item[type].map(item => item.value)
      } else {
        checkedItem[type] = []
      }

      Object.keys(this.checkedList).forEach(region => {
        Object.keys(checkedItem).forEach(key => {
          if (key !== type) {
            this.checkedList[region][key] = []
          }
        })
      })
      this.checkedData = checkedItem
    }
  }
}
</script>
<style scoped>
</style>
