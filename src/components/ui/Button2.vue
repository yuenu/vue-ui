<template>
  <a href="#" class="button">
    <span class="button__text">{{ text }}</span>
  </a>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  props: {
    text: {
      type: String,
      default: 'CLICK'
    }
  }
})
</script>

<style lang="scss" scoped>
$btnWidth: 120px;
$btnHeight: 40px;
$btnBackground:#d3a638;

.button {
  display: inline-block;
  background: transparent;
  border: 2px solid $btnBackground;
  color: rgb(231, 56, 56);
  width: $btnWidth;
  height: $btnHeight;
  font-size: 16px;
  font-weight: 600;
  transition: 0.3s all ease-out;
  overflow: hidden;
  position: relative;

  &:hover {
    color: #fff;
  }

  &:before {
    content: "";
    width: $btnWidth;
    height: $btnHeight;
    background: $btnBackground;
    display: inline-block;
    transform: translateX(100%);
    transition: 0.25s all ease-in-out;
  }

  &:hover::before {
    transform: translateX(0%);
  }

  &__text {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
}
</style>
