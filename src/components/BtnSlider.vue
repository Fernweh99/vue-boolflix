<template>
    <i v-if="direction=='left'" class="bi bi-chevron-compact-left"></i>
    <i v-else class="bi bi-chevron-compact-right"></i>
</template>

<script>
export default {
  name: "BtnSlider",
  props: {
    direction: String,
  }
}
</script>

<style lang="scss">
@import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.9.1/font/bootstrap-icons.css");
i {
  position: absolute;
  font-size: 90px;
  z-index: 1;
  color: white;
  cursor: pointer;
  &.bi-chevron-compact-left {
    left: -100px;
    top: 50%;
    transform: translateY(-50%);
  }
  &.bi-chevron-compact-right {
    right: -100px;
    top: 50%;
    transform: translateY(-50%);
  }
}
</style>