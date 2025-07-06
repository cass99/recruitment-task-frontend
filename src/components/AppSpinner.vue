<template>
  <div
      v-if="loading"
      class="Spinner"
  >
    <div class="Spinner__loading"></div>
  </div>
</template>

<script setup>
defineProps({
  loading: {
    type: Boolean,
    default: false
  }
})
</script>

<style scoped lang="scss">
  .Spinner {
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    z-index: 9999;

    &__ {
      &loading {
        width: 60px;
        height: 60px;
        border-radius: 50%;
        border: 8px solid $surface;
        border-top-color: $black;
        animation: loading 1s linear infinite;

        @include gt-tablet-portrait {
          width: 100px;
          height: 100px;
          border: 10px solid $surface;
          border-top-color: $black;
        }
      }
    }
  }

  @keyframes loading {
    to {
      transform: rotate(360deg);
    }
  }
</style>