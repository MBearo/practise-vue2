<template>
  <div>
    <el-button @click="() => chengeType('area')">
      地区
    </el-button>
    <el-button @click="() => chengeType('ring')">
      商圈
    </el-button>
    <AreaList
      v-show="type==='area'"
      :list="data.area"
      :checked-list="checkedData.area"
      @checked="(e)=>handleChecked(e,'area')"
    />
    <AreaList
      v-show="type==='ring'"
      :list="data.ring"
      :checked-list="checkedData.ring"
      @checked="(e)=>handleChecked(e,'ring')"
    />
  </div>
</template>
<script>
import AreaList from './AreaList.vue'
export default {

  components: {
    AreaList
  },

  mixins: [],
  props: {
    data: {
      type: Object,
      default: () => {}
    },
    checkedData: {
      type: Object,
      default: () => {}
    }
  },

  data () {
    return {
      type: 'area'
    }
  },

  computed: {

  },

  watch: {

  },

  created () {

  },

  mounted () {

  },

  methods: {
    chengeType (type) {
      this.type = type
      console.log('type', this.type)
    },
    handleChecked ({ event, item }, type) {
      this.$emit('checked', { event, item, type })
    }
  }
}
</script>
<style scoped>
</style>
