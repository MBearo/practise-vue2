<template>
  <div>
    <el-checkbox
      v-for="(item,index) in list"
      :key="item.value"
    >
      {{ item.label }}
      <el-button @click="()=>changeRegion(index)">
        切换地区
      </el-button>
    </el-checkbox>
    <Tab
      :data="areaData"
      :checked-data="checkedData"
      @checked="handleChecked"
    />
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
      areaData: [],
      checkedList: {},
      checkedData: {
        area: [],
        ring: []
      }
    }
  },

  computed: {

  },

  watch: {

  },

  created () {
    this.areaData = this.list[0]
  },

  mounted () {

  },

  methods: {
    changeRegion (index) {
      this.areaData = this.list[index]
    },
    handleChecked (e) {
      console.log(e)
    }
  }
}
</script>
<style scoped>

</style>
