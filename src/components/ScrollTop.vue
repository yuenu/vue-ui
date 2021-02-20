<template>
  <div
    ref="scrollBtn"
    class="scrollToTop"
    @click="scrollToTop(300)"
  >
    <span />
    <span />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  mounted () {
    window.onscroll = () => {
      this.scrollButtonShow()
    }
  },

  methods: {
    scrollToTop (duration: number) {
      const scrollElement = document.scrollingElement as HTMLElement
      // cancel if already on top
      if (scrollElement.scrollTop === 0 && document.scrollingElement === null) { return }

      const totalScrollDistance = scrollElement.scrollTop
      let scrollY = totalScrollDistance
      let oldTimestamp: number | null = null

      function step (newTimestamp: number | null) {
        if (oldTimestamp !== null && newTimestamp !== null) {
        // if duration is 0 scrollY will be -Infinity
          scrollY -=
          (totalScrollDistance * (newTimestamp - oldTimestamp)) / duration
          if (scrollY <= 0) return (scrollElement.scrollTop = 0)
          scrollElement.scrollTop = scrollY
        }
        oldTimestamp = newTimestamp
        window.requestAnimationFrame(step)
      }
      window.requestAnimationFrame(step)
    },

    scrollButtonShow () {
      const scrollBtn = this.$refs.scrollBtn as HTMLElement

      if (
        document.body.scrollTop > 50 ||
      document.documentElement.scrollTop > 50
      ) {
        scrollBtn.style.display = 'flex'
      } else {
        scrollBtn.style.display = 'none'
      }
    }
  }
})
</script>

<style lang="scss" scoped>
$borderColor: darkgoldenrod;
$arrowColor: rgb(147, 33, 33);

.scrollToTop {
  position: fixed;
  width: 50px;
  height: 50px;
  right: 2%;
  bottom: 2%;
  border-radius: 50%;
  border: 2px solid $borderColor;
  display: none;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  cursor: pointer;
  z-index:999;

  & span {
    width: 15px;
    height: 2px;
    background: $arrowColor;
    border-radius: 2px;
    display: inline-block;
    transition: 0.3s transform ease;
  }

  & span:first-child {
    transform: translateX(3px) rotate(-50deg);
  }

  & span:last-child {
    transform: translateX(-3px) rotate(50deg);
  }

  &:hover span:first-child {
    transform: translate(3px, -3px) rotate(-50deg);
  }

  &:hover span:last-child {
    transform: translate(-3px, -3px) rotate(50deg);
  }
}

@media (max-width: 800px) {
  .scrollToTop {
    background: $borderColor;
  }
}
</style>
