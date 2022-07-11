<template>
  <div>
    <el-checkbox-group v-model="checkedCities">
      <Checkbox
        v-for="item in list"
        :key="item.value"
        :is-area="isArea"
        :item="item"
        :area-checked-list="areaCheckedList"
        :ring-checked-list="ringCheckedList"
        @change="(event) => handleCheckAllChange(event, item)"
      />
    </el-checkbox-group>
    <Tab
      :is-area="isArea"
      :area-list="areaList"
      :ring-list="ringList"
      :area-checked-list="areaCheckedList"
      :ring-checked-list="ringCheckedList"
      @typeChange="typeChange"
      @checkedChange="checkedChange"
    />
  </div>
</template>
<script>
import { data } from './data'
import Tab from './Tab.vue'
import Checkbox from './Checkbox.vue'

export default {

  components: {
    Tab,
    Checkbox
  },

  mixins: [],
  props: {

  },

  data () {
    return {
      list: data,
      checkedCities: [],

      //   indeterminate: false,
      checkAll: false,

      areaList: [],
      areaCheckedList: [],
      ringList: [],
      ringCheckedList: [],

      isArea: true
    }
  },

  computed: {
    indeterminate: (e) => {
      console.log(e)
      return true
    }
  },

  watch: {

  },

  created () {
    this.areaList = this.list[0].area
    this.ringList = this.list[0].ring
  },

  mounted () {

  },

  methods: {
    handleCheckAllChange (event, listItem) {
      console.log('event', event, listItem)
      if (event) {
        this.isArea ? this.areaCheckedList = listItem.area.map(v => v.value) : this.ringCheckedList = listItem.ring.map(v => v.value)
      } else {
        this.isArea ? this.areaCheckedList = [] : this.ringCheckedList = []
      }
    },
    typeChange (e) {
      this.isArea = e
    },
    checkedChange (e, item, index, isArea) {
      if (e) {
        isArea
          ? this.areaCheckedList.push(item.value)
          : this.ringCheckedList.push(item.value)
      } else {
        isArea
          ? this.areaCheckedList = this.areaCheckedList.filter(v => v !== item.value)
          : this.ringCheckedList = this.ringCheckedList.filter(v => v !== item.value)
      }
    }

  }
}
</script>
<style scoped>
</style>
