<template>
  <div
    :class="['hamburger', { open: menuOpen }]"
    @click="menuClicked"
  >
    <div class="hamburger__inbox"></div>
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue'
export default defineComponent({
  data () {
    return {
      menuOpen: false
    }
  },
  methods: {
    menuClicked () {
      this.menuOpen = !this.menuOpen
    }
  }
})
</script>
<style lang="scss" scoped>
$btnSize:50px;
$hamburgerburgerColor: #fff;
$hamburgerburgerHeight: 3px;

.hamburger {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  width: $btnSize;
  height: $btnSize;
  cursor: pointer;
  border: 3px solid $hamburgerburgerColor;
}

.hamburger__inbox {
  width: $btnSize - $btnSize * 0.4;
  height: $hamburgerburgerHeight;
  background: $hamburgerburgerColor;
  transition: all 0.3s ease-in-out;
}

.hamburger__inbox::before,
.hamburger__inbox::after {
  content: "";
  position: absolute;
  width: $btnSize - $btnSize * 0.4;
  height: $hamburgerburgerHeight;
  background: $hamburgerburgerColor;
  transition: all 0.3s ease-in-out;
}

.hamburger__inbox::before {
  transform: translate(-50% ,-$btnSize * 0.2);
}

.hamburger__inbox::after {
  transform: translate(-50% ,$btnSize * 0.2);
}

/* ANIMATION */
.hamburger.open .hamburger__inbox {
  transform: translateX(-$btnSize);
  background: transparent;
  box-shadow: none;
}

.hamburger.open .hamburger__inbox::before {
  transform: rotate(45deg) translate($btnSize * 0.5, -$btnSize * 0.5);
}

.hamburger.open .hamburger__inbox::after {
  transform: rotate(-45deg) translate($btnSize * 0.5, $btnSize * 0.5);
}

</style>
