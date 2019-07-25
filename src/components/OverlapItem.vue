<template>
  <li
      v-bind:key="item.id"
      v-on:click="handleSelect"
  >{{item.label}}</li>
</template>

<script>
export default {
  name: 'OverlapItem',
  props: {
    item: {
      type: Object,
      required: true
    }
  },
  methods: {
    handleSelect: function () {
      this.$emit('selectItem', this.item)
    }
  }
}
</script>