<template>
  <button class="siri-button" :class="classes" :disabled="disabled">
    <span v-if="loading" class="siri-loadingIndicator"></span>
    <slot/>
  </button>
</template>

<script lang="ts">
import {computed} from 'vue'
export default {
  props: {
    theme: {
      type: String,
      default: "button"
    },
    size: {
      type: String,
      default: "normal",
    },
    level:{
      type: String,
      default: "normal",
    },
    disabled:{
      type: Boolean,
      default: false
    },
    loading:{
      type: Boolean,
      default:false
    }
  },
  setup(props) {
    const {theme, size, level} = props
    const classes = computed(() => {

      return {
        [`siri-theme-${theme}`]: theme,
        [`siri-size-${size}`]: size,
        [`siri-level-${level}`]: level,
      };
    });
    return {classes}
  }
};
</script>

<style lang="scss">
$h: 32px;
$border-color: #d9d9d9;
$color: #333;
$blue: #40a9ff;
$radius: 4px;
$red: red;
$grey:grey;
.siri-button {
  box-sizing: border-box;
  height: $h;
  padding: 0 12px;
  cursor: pointer;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  white-space: nowrap;
  background: white;
  color: $color;
  border: 1px solid $border-color;
  border-radius: $radius;
  box-shadow: 0 1px 0 fade-out(black, 0.95);
  transition: background 250ms;

  & + & {
    margin-left: 8px;
  }

  &:hover,
  &:focus {
    color: $blue;
    border-color: $blue;
  }

  &:focus {
    outline: none;
  }

  &::-moz-focus-inner {
    border: 0;
  }

  &.siri-theme-link {
    border-color: transparent;
    box-shadow: none;
    color: $blue;

    &:hover,
    &:focus {
      color: lighten($blue, 10%)
    }
  }

  &.siri-theme-text {
    border-color: transparent;
    box-shadow: none;
    color: inherit;

    &:hover,
    &:focus {
      background: darken(white, 5%);
    }
  }
  &.siri-size-big {
    font-size: 24px;
    height: 48px;
    padding: 0 16px;
  }

  &.siri-size-small {
    font-size: 12px;
    height: 20px;
    padding: 0 4px;
  }

  &.siri-theme-button{
    &.siri-level-main{
      background: $blue;
      color: white;
      border-color: $blue;
      &:hover,
      &:focus{
        background: darken($blue, 10%);
        border-color: darken($blue, 10%);
      }
    }
    &.siri-level-danger{
      background: $red;
      border-color: $red;
      color:white;
      &:hover,
      &:focus{
        background: darken($red, 10%);
        border-color: darken($red, 10%);
      }
    }
  }
  &.siri-theme-link{
    &.siri-level-danger{
      color: $red;
      &:hover,
      &:focus{
        color: darken($red, 10%)
      }
    }
  }
  &.siri-theme-text{
    &.siri-level-main{
      color: $blue;
      &:hover,
      &:focus{
        color: darken($blue, 10%)
      }
    }
    &.siri-level-danger{
      color: $red;
      &:hover,
      &:focus{
        color: darken($red, 10%)
      }
    }
  }
  &.siri-theme-button{
    &[disabled]{
      cursor: not-allowed;
      color: grey;
      &:hover{
        border-color: $grey;
      }
    }
  }
  &.siri-theme-link, &.siri-theme-text{
    &[disabled]{
      cursor: not-allowed;
      color: $grey;
    }
  }
  > .siri-loadingIndicator{
    width: 14px;
    height: 14px;
    display: inline-block;
    margin-right: 4px;
    border-radius: 8px;
    border-color: $blue $blue $blue transparent;
    border-style: solid;
    border-width: 2px;
    animation: siri-spin 1s infinite linear;
  }
}
@keyframes siri-spin {
  0%{transform:rotate(0deg)}
  100%{transform: rotate(360deg)}
}

</style>