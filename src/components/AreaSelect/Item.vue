<template>
  <el-checkbox-group :value="checkedList">
    <el-checkbox
      v-for="(item, index) in list"
      :key="item.value"
      :label="item.value"
      @change="e => handleChange(e, item, index)"
    >
      {{ item.label }}
    </el-checkbox>
  </el-checkbox-group>
</template>
<script>
export default {

  components: {

  },

  mixins: [],
  props: {
    list: {
      type: Array,
      default: () => []
    },
    checkedList: {
      type: Array,
      default: () => []
    },
    isArea: {
      type: Boolean,
      default: true
    }
  },

  data () {
    return {
      // checkedItems: []
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
    handleChange (e, item, index) {
      console.log('e', e, item, index, this.isArea)
      this.$emit('change', e, item, index, this.isArea)
    }
  }
}
</script>
<style scoped>
</style>
