<template>
  <div>
    <el-radio-group
      :value="isArea"
      @change="typeChange"
    >
      <el-radio :label="true">
        区域
      </el-radio>
      <el-radio :label="false">
        商圈
      </el-radio>
    </el-radio-group>
    <Item
      v-show="isArea"
      :list="areaList"
      :checked-list="areaCheckedList"
      :is-area="true"
      @change="checkedChange"
    />
    <Item
      v-show="!isArea"
      :list="ringList"
      :checked-list="ringCheckedList"
      :is-area="false"
      @change="checkedChange"
    />
  </div>
</template>
<script>
import Item from './Item.vue'

export default {

  components: {
    Item
  },

  mixins: [],
  props: {
    areaList: {
      type: Array,
      default: () => []
    },
    ringList: {
      type: Array,
      default: () => []
    },
    isArea: {
      type: Boolean,
      default: true
    },
    areaCheckedList: {
      type: Array,
      default: () => []
    },
    ringCheckedList: {
      type: Array,
      default: () => []
    }
  },

  data () {
    return {
      checkedCities: []
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
    typeChange (e) {
      this.$emit('typeChange', !e)
    },
    checkedChange (e, item, index, isArea) {
      this.$emit('checkedChange', e, item, index, isArea)
    }
  }
}
</script>
<style scoped>
</style>
