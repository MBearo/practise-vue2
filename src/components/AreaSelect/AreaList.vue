<template>
  <el-checkbox-group :value="checkedList">
    <el-checkbox
      v-for="item in list"
      :key="item.value"
      @change="(e)=>handleChecked(e,item)"
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
    checkedList: {
      type: Array,
      default: () => []
    },
    list: {
      type: Array,
      default: () => []
    }
  },

  data () {
    return {

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
    handleChecked (event, item) {
      console.log('first', event, item)
      this.$emit('checked', { event, item })
    }
  }
}
</script>
<style scoped>
</style>
