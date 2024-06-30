<script lang="ts" setup>
const showSlideover = ref(false);
</script>

<template>
  <div class="w-full h-screen overflow-hidden">
    <!-- 小型屏幕显示 -->
    <div class="h-full block md:hidden">
      <NuxtLayout sticky name="between-middle">
        <template #left>
          <UButton
            @click="showSlideover = true"
            icon="i-codicon-layout-sidebar-left-off"
            variant="ghost"
          ></UButton>
        </template>
        <template #middle>
          <h1>DataHub</h1>
        </template>
        <template #right>
          <UserMenu></UserMenu>
        </template>
      </NuxtLayout>

      <USlideover side="left" v-model="showSlideover">
        <SidebarContainer v-model="showSlideover"></SidebarContainer>
      </USlideover>
    </div>

    <!-- 大型屏幕显示 -->
    <div class="hidden h-full md:grid md:grid-cols-[260px_5fr]">
      <div class="top-0">
        <SidebarContainer v-model="showSlideover"></SidebarContainer>
      </div>

      <main class="overflow-auto bg-white dark:bg-black">
        <NuxtLayout sticky name="between-middle">
          <template #left>
            <h1>DataHub</h1>
          </template>
          <template #right>
            <UserMenu></UserMenu>
          </template>
        </NuxtLayout>

        <UContainer class="h-full">
          <NuxtWelcome></NuxtWelcome>
        </UContainer>
      </main>
    </div>
  </div>
</template>

<style scoped></style>
