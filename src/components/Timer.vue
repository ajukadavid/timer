<template>
<div>
     <div class="count">12</div>
    <div class="label">{{label}}</div>
  
</div>
   
</template>

<script setup lang="ts">

defineProps<{ label: string }>()

</script>

<style scoped>
.count {
    font-size: 4rem;
    font-weight: 800;

}
</style>