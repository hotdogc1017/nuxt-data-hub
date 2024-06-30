<script setup lang="ts">
const prop = defineProps<{
  sticky?: boolean;
}>();
</script>

<template>
  <div
    :class="`${prop.sticky ? 'sticky top-0 z-10' : 'relative'}`"
    class="min-h-[60px] bg-inherit flex justify-center items-center mx-4"
  >
    <div class="absolute left-0 h-full flex items-center">
      <slot name="left"></slot>
    </div>
    <div>
      <slot name="middle"></slot>
    </div>
    <div class="absolute right-0 h-full flex items-center">
      <slot name="right"></slot>
    </div>
  </div>
</template>

<style scoped></style>
