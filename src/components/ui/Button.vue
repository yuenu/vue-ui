<template>
  <a
    class="button"
    href="#"
    target="new"
  >
    <span class="button__inner">
      <span class="button__arrows">
        <span class="button__arrow">→</span>
        <span class="button__arrow">→</span>
      </span>
      <span class="button__text">{{ text }}</span>
    </span>
  </a>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  props: {
    text: {
      type: String,
      default: 'click'
    }
  }
})
</script>

<style lang="scss" scoped>
$backgroundColor: #d3a638;
$btnWidth:120px;
$btnHeight:40px;

.button {
  display: inline-block;
  position: relative;
  color: #121212;
  background: none;
  width: $btnWidth;
  height: $btnHeight;
  padding: 13px 17px;
  text-decoration: none;
}

.button::before {
  content: "";
  width: $btnWidth;
  height: $btnHeight;
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  border: 2px solid #e2ba53;
  z-index: 2;
  transform: translate(-4px, -4px);
  transition: 0.32s all cubic-bezier(0.58, 0.05, 0.22, 0.98);

}

.button::after {
  content: "";
  width: $btnWidth + 1px;
  height: $btnHeight + 1px;
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  background: $backgroundColor;
  z-index: 1;
  transform: translate(4px, 4px);
  transition: 0.32s all cubic-bezier(0.58, 0.05, 0.22, 0.98);
  box-shadow:2px 2px 2px rgb(113, 113, 113);
}

.button:hover::before{
  transform: translate(0px, 0px);
}

.button:hover::after {
  transform: translate(2px, 2px);
}

.button__inner {
  display: flex;
  height: 100%;
  position: relative;
  align-items: center;
  z-index: 3;
  justify-content: center;
}

.button__arrows {
  font-size: 16px;
  margin-right: 10px;
  margin-top: -2px;
  overflow: hidden;
  position: relative;
}

.button__arrow:first-child {
  transform: translate(0%);
  display: inline-block;
  position: absolute;
  left: 0;
  opacity: 1;
  transition: 0.5s all ease;
}

.button:hover .button__arrow:first-child {
  transform: translate(100%);
  opacity: 0;
}

.button__arrow:last-child {
  transform: translate(-100%);
  opacity: 1;
  transition: 0.5s all ease-out;
}

.button:hover .button__arrow:last-child {
  transform: translate(0%);
}

.button__arrow {
  display: inline-block;
}

.button__text {
  font-size: 16px;
  display: inline-block;
  margin-top:2px;
  font-weight: 600;
  color: #000;
  transition: transform 0.15s ease-out;
}

.button:hover .button__text {
  transform: translateZ(0) skewX(-15deg);
}

@media (max-width: 476px) {
  .button__text {
    font-size: 15px;
  }
}
</style>
