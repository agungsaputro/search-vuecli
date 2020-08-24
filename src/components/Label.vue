<template>
    <span>{{ text }}</span>
</template>
<script>
import { technologies } from '../data'
export default {
    name: 'Label',
  props: {
    tech: {
      type: String,
      require: true
    }
  },
  computed: {
    text: function() {
      return technologies[this.tech].label
    } 
  }
}
</script>