<template>
    <button class='siri-switch' @click="toggle" :class="{'siri-checked': value}">
      <span></span>
    </button>
</template>
<script lang="ts">

export default {
  props: {
    value: Boolean
  },
  setup(props, context) {
    const toggle = ()=>{
      context.emit('update:value', !props.value)
    }
    return {toggle};
  }
};
</script>

<style lang="scss">
$h: 22px;
$h2: $h - 4px;
.siri-switch  {
  height: $h;
  width: $h*2;
  border: none;
  background: #bfbfbf;
  border-radius: $h/2;
  position: relative;
  > span {
    position: absolute;
    top: 2px;
    left: 2px;
    height: $h2;
    width: $h2;
    background: white;
    border-radius: $h2 / 2;
    transition: all 250ms;
    }
    &.siri-checked {
      background: #FF879D;

      > span {
        left: calc(100% - #{$h2} - 2px)
      }
    }
    &:focus{
      outline: none;
    }
    &:active{
      > span{width: $h2 + 4px;}
    }
    &.siri-checked:active{
      > span{width: $h2 + 4px;
        margin-left: -4px;
      }
    }
}
</style>