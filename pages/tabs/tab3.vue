<template>
  <section>
    <div class="flex flex-col gap-8">
      <div class="flex h-10 items-center justify-between self-stretch">
        <div class="flex items-start gap-4">
          <button
            class="font-medium transition-colors duration-200"
            :class="[
              route.path.match(`/tabs/tab3/subtab1`)
                ? 'cursor-default text-blue-400'
                : 'text-blue-900 hover:opacity-80',
            ]"
            @click="changeSubTab('subtab1')"
          >
            <div class="flex items-center justify-center gap-2">
              <span>Sub tab 1</span>
            </div>
          </button>

          <button
            class="font-medium transition-colors duration-200"
            :class="[
              route.path.match(`/tabs/tab3/subtab2`)
                ? 'cursor-default text-blue-400'
                : 'text-blue-900 hover:opacity-80',
            ]"
            @click="changeSubTab('subtab2')"
          >
            <div class="flex items-center justify-center gap-2">
              <span>Sub tab 2</span>
            </div>
          </button>
        </div>
      </div>

      <div>
        <NuxtPage />
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
  const route = useRoute()

  function changeSubTab(path: string) {
    if (route.path.match(`/tabs/tab3/${path}`)) {
      return
    }

    navigateTo(`/tabs/tab3/${path}`)
  }

  if (route.path === '/tabs/tab3') {
    navigateTo('/tabs/tab3/subtab1', { redirectCode: 301 })
  }
</script>
