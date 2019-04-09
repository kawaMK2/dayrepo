<template lang="pug">
  div.btn-group.yesno
    label(@click="setYes" :class="{active: value===true}").btn.btn-outline-secondary.selection はい
    label(@click="setNo" :class="{active: value===false}").btn.btn-outline-secondary.selection いいえ
</template>

<script>
export default {
  name: 'YesNoInput',
  props: {
    value: { type: Boolean, required: true }
  },
  updated: function() {
    this.$emit('input', {
      value: this.value
    })
  },
  methods: {
    setYes: function() {
      this.value = true
    },
    setNo: function() {
      this.value = false
    }
  }
}
</script>

<style scoped>
.yesno {
  width: 150px;
}

.selection {
  white-space: nowrap;
  padding-left: 0;
  padding-right: 0;
  align-items: center;
  width: 50%;
  /*font-size: 12px;*/
}
</style>
