<template>
    <div class="item">
      <h2>{{ baby.nm }}</h2>
    </div>
</template>

<script setup>
const props = defineProps({
  baby: Object,
})
</script>
 
<style scoped>

</style>