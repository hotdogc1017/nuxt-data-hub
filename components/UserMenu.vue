<script lang="ts" setup>
// import { type DropdownItem } from "#ui/types/dropdown";
const dropdownItems = [
  [
    {
      label: "hotdog",
      slot: "account",
      disabled: true,
    },
    {
      label: "设置",
      icon: "i-codicon-settings-gear",
    },
  ],

  [
    {
      label: "注销",
      slot: "logout",
      icon: "i-codicon-sign-out",
    },
  ],
];
const colorMode = useColorMode();
const isDark = computed({
  get() {
    return colorMode.value === "dark";
  },
  set() {
    colorMode.preference = colorMode.value === "dark" ? "light" : "dark";
  },
});
</script>

<template>
  <UDropdown
    :items="dropdownItems"
    :ui="{ item: { disabled: 'cursor-text select-text opacity-1' } }"
  >
    <UAvatar
      src="https://gitee.com/hotdogc/file-library/raw/master/%E5%8F%AF%E7%88%B1%E4%BF%AE%E5%8B%BE.awebp"
    ></UAvatar>

    <template #account="{ item: { label } }">
      <span class="truncate opacity-50 text-gray-900 dark:text-white"
        >账户名: {{ label }}</span
      >

      <div class="flex-shrink-0 h-4 w-4 ms-auto">
        <UButton
          class=""
          variant="soft"
          :padded="false"
          size="xs"
          :icon="
            isDark ? 'i-heroicons-moon-20-solid' : 'i-heroicons-sun-20-solid'
          "
          aria-label="Theme"
          @click="isDark = !isDark"
        ></UButton>
      </div>
    </template>

    <template #logout="{ item: { icon, label } }">
      <span class="truncate font-mono text-sm text-red-400">{{ label }}</span>
      <UIcon
        class="flex-shrink-0 h-4 w-4 text-gray-400 dark:text-gray-500 ms-auto"
        :name="icon"
      ></UIcon>
    </template>

    <template #item="{ item: { icon, label } }">
      <span class="truncate font-mono text-sm">{{ label }}</span>
      <UIcon
        class="flex-shrink-0 h-4 w-4 text-gray-400 dark:text-gray-500 ms-auto"
        :name="icon"
      ></UIcon>
    </template>
  </UDropdown>
</template>

<style scoped></style>
