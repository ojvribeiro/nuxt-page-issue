<template>
  <li>
    <button
      class="w-full border-b-2 py-6 transition-all hover:text-blue-400"
      :class="[props.active && 'border-blue-400 text-blue-400']"
      v-bind="$attrs"
    >
      <slot />
    </button>
  </li>
</template>

<script setup lang="ts">
  const props = withDefaults(
    defineProps<{
      active: boolean
    }>(),
    {
      active: false,
    }
  )

  defineOptions({
    inheritAttrs: false,
  })
</script>
