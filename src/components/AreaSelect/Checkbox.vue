<template>
  <el-checkbox
    v-model="checkAll"
    :indeterminate="indeterminate"
    :label="item.label"
    @change="(event) => handleCheckAllChange(event, item)"
  >
    {{ item.label }}
    <el-button>
      >
    </el-button>
  </el-checkbox>
</template>
<script>
export default {

  components: {

  },

  mixins: [],
  props: {
    isArea: {
      type: Boolean,
      default: true
    },
    item: {
      type: Object,
      default: () => { }
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
      //   indeterminate: false,
      checkAll: false
    }
  },

  computed: {
    indeterminate () {
      if (this.isArea) {
        return !!(this.areaCheckedList.length && this.areaCheckedList.length < this.item.area.length)
      } else {
        return !!(this.ringCheckedList.length && this.ringCheckedList.length < this.item.ring.length)
      }
    }
  },

  watch: {

  },

  created () {

  },

  mounted () {

  },

  methods: {
    handleCheckAllChange (event, listItem) {
      this.$emit('change', event, listItem)
    }
  }
}
</script>
<style scoped>
</style>
