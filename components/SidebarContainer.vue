<script lang="ts" setup>
const showSidebar = defineModel();
</script>

<template>
  <nav class="h-full overflow-auto bg-gray-100 dark:bg-gray-900">
    <NuxtLayout sticky name="between-middle">
      <template #left>
        <UTooltip :text="`关闭侧边栏`" :openDelay="500">
          <UButton
            @click="showSidebar = false"
            variant="ghost"
            color="gray"
            icon="i-codicon-layout-sidebar-left-off"
          ></UButton>
        </UTooltip>
      </template>
      <template #right>
        <UTooltip text="添加任务" :openDelay="500">
          <UButton variant="ghost" color="gray" icon="i-codicon-add"></UButton>
        </UTooltip>
      </template>
    </NuxtLayout>

    <UContainer class="h-full">
      <UButton>刷新</UButton>
    </UContainer>

    <div class="h-10 sticky bottom-0 bg-inherit px-4 flex items-center gap-4">
      <ULink
        inactiveClass="text-gray-400 dark:text-gray-500 cursor-text select-text"
        ><span class="text-xs">当前版本: v0.0.0</span></ULink
      >
      <ULink to="/changelogs" active-class="text-primary"
        ><span class="text-xs">更新日志</span></ULink
      >
    </div>
  </nav>
</template>

<style scoped></style>
