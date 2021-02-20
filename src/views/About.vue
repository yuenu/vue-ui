<template>
  <div class="ui">
    <div class="box">
      <span class="box__list">1.</span>
      <Spinner />
    </div>
    <div class="box">
      <span class="box__list">2.</span>
      <Button />
    </div>
    <div class="box">
      <span class="box__list">3.</span>
      <Button2 />
    </div>
    <div class="box">
      <span class="box__list">4.</span>
      <Hamburger />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Spinner from '@/components/ui/Spinner.vue'
import Button from '@/components/ui/Button.vue'
import Button2 from '@/components/ui/Button2.vue'
import Hamburger from '@/components/ui/HamburgerMenu.vue'

export default defineComponent({
  components: {
    Spinner,
    Button,
    Button2,
    Hamburger
  }
})
</script>

<style lang="scss" scoped>
.ui {
  border: 1px solid red;
  min-height: 100vh;
  background:lightgray;
}

.box {
  display:flex;
  align-items:center;
  justify-content: center;
  height:fit-content;
  border-bottom:5px solid rgb(233, 233, 233);
  padding:20px 0;

  &__list {
    margin-right:10px;
  }
}
</style>
