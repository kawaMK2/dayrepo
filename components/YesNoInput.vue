<template lang="pug">
  div
    div(v-if="value===null||value===undefined").btn-group.yesno
      label(@click="setYes").btn.btn-outline-secondary.selection はい
      label(@click="setNo").btn.btn-outline-secondary.selection いいえ
    div(v-else-if="value").btn-group.yesno
      label(@click="setYes").btn.btn-outline-secondary.selection.active はい
      label(@click="setNo").btn.btn-outline-secondary.selection いいえ
    div(v-else).btn-group.yesno
      label(@click="setYes").btn.btn-outline-secondary.selection はい
      label(@click="setNo").btn.btn-outline-secondary.selection.active いいえ
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
