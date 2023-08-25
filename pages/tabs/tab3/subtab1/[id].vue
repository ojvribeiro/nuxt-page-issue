<template>
  <div class="flex flex-col gap-4">
    Subtab content:

    <pre>{{ data }}</pre>
  </div>
</template>

<script setup lang="ts">
  const route = useRoute()

  const { data } = await useFetch(
    `https://jsonplaceholder.typicode.com/todos/${route.params.id}`
  )
</script>
