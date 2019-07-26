<template>
  <div class="selector">
    <span class="current" v-on:click="handleShowOptions">{{ getNombreselected }}</span>
    <ul class="desplegado" v-if="showFilters">
      <OverlapItem
        v-for="item in options"
        v-bind:item="item"
        v-bind:key="item.id"
        v-on:selectItem="handleSelect"/>
    </ul>
  </div>
</template>

<script>
import OverlapItem from './OverlapItem'

export default {
  name: 'OverlapComponent',
  props: {
    options: {
      type: Array,
      required: true
    }
  },
  components: {
    OverlapItem
  },
  data: function () {
    return ({
      selected: null,
      showFilters: false
    })
  },
  created: function () {
    this.selected = this.options[0]
  },
  destroyed() {
    // Clear event capture
    if (this.showFilters) {
      this.close()
    }
  },
  methods: {
    handleSelect: function (item) {
      this.selected = item
      this.close()
    },
    handleShowOptions: function () {
      this.showFilters ? this.close() : this.open()
    },
    open() {
      this.showFilters = true;
      // addOutsideClickListener
      setTimeout(() => {
        document.addEventListener('click', this.clickOutside, false)
      }, 100)
    },
    clickOutside(event) {
      if (this.$el && !this.$el.contains(event.target)) {
        this.close()
      }
    },
    close() {
      this.showFilters = false
      // removeOutsideClickListener
      document.removeEventListener('click', this.clickOutside, false)
    }
  },
  computed: {
    getNombreselected() {
      return this.selected ? this.selected.label : 'Selecciona'
    }
  }
}
</script>