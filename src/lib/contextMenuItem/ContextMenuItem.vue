<template>
  <li @click="handler" :style="{opacity:this.disabled?'0.5':'1'}">
    <slot></slot>
  </li>
</template>

<script>
  import Bus from '../contextMenu/EventBus'

  export default {
    name: "ContextMenuItem",
    props: {
      select: {
        type: String | Number | Object,
        default: ''
      },
      disabled: {
        type: Boolean,
        default: false
      }
    },
    methods: {
      handler() {
        if (!this.disabled) {
          Bus.$emit('selectEmitted', this.select)
        }
      }
    }
  }
</script>

<style scoped>
  li {
    display: block;
    min-width: 3rem;
    height: 2rem;
    line-height: 2rem;
    font-size: 0.8rem;
    text-align: center;
    margin: 0;
  }

  li:hover {
    background-color: darkgrey;
    cursor: pointer;
  }
</style>
