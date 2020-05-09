<template>
  <div class="tascan">
    Some tascan Text

    <div>
      <slot />
    </div>
  </div>
</template>

<script>
export default {
    
}
</script>

<style scoped>
  .tascan {
    padding: 50px;
    border: 5px dotted black;
  }
</style>