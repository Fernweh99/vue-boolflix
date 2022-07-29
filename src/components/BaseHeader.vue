<template>
  <header>
    <div class="container h-100">
      <div class="h-100 row align-items-center">
        <div class="col">
          <h3 class="text-danger">BoolFlix</h3>
        </div>
        <div class="col text-end">
          <SelectComponent @btn-search-click="emitSearchText"/>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
import SelectComponent from "./SelectComponent.vue"

export default {
  name: "BaseHeader",
  components: {
    SelectComponent,
  },
  methods: {
    emitSearchText (search) {
    this.$emit("btn-search-click", search)
    }
  }
}
</script>

<style>
  header {
    z-index: 10;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    height: 70px;
    background-color: rgba(42, 42, 42, 0.577);

  }
</style>