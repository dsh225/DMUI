<template>
    <div class="dm__select">
        <select :class="[{'is-right': right}]" v-model="selectVal" :disabled="disabled">
          <option v-for="(item,index) in data" :value="item.value" :key="index">{{item.name}}</option>
        </select>
    </div>
</template>

<script>

export default {
  name: 'dm-select',
  props: {
    data: {
      type: Array,
      required: true
    },
    right: {
      type: Boolean,
      default: false
    },
    disabled: {
      type: Boolean,
      default: false
    },
    value: [String, Number, Object, Boolean]
  },
  data () {
    return {
      selectVal: ''
    }
  },
  watch: {
    value (val) {
      this.selectVal = val
    },
    selectVal (val) {
      this.$emit('change', val)
      this.$emit('input', val)
    }
  },
  created () {
    if (typeof this.value !== 'undefined') {
      this.selectVal = this.value
    }
  }
}
</script>

<style scoped lang="scss">

</style>
