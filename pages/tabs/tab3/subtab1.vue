<template>
  <section class="flex flex-col gap-8">
    <div class="flex flex-col gap-4">
      <!-- Card -->
      <ClientOnly>
        <div
          v-for="i in 5"
          class="relative flex flex-col overflow-hidden rounded-2xl border transition-colors hover:border-gray-500-400"
          :class="[
            currentActiveAccordion === i
              ? '!border-blue-400'
              : 'border-gray-300',
          ]"
        >
          <button
            class="group flex items-center justify-between gap-4 self-stretch p-4"
            @click="handleChangeAccordion(i)"
          >
            Accordion {{ i }}
          </button>

          <div v-if="currentActiveAccordion === i" class="p-4 text-start">
            <div class="-my-4 border-b" />

            <div class="mt-8">
              <Suspense>
                <!-- Loading state -->
                <template #fallback>
                  <Suspense>
                    <div>Loading...</div>
                  </Suspense>
                </template>

                <!-- Rendered page -->
                <div>
                  <NuxtPage />
                </div>
              </Suspense>
            </div>
          </div>
        </div>
      </ClientOnly>
    </div>
  </section>
</template>

<script setup lang="ts">
  const currentActiveAccordion = ref<number | null>(null)

  function handleChangeAccordion(id: number) {
    if (currentActiveAccordion.value !== id) {
      navigateTo(`/tabs/tab3/subtab1/${id}`)

      currentActiveAccordion.value = id

      return
    }

    currentActiveAccordion.value = null
  }

  onBeforeRouteLeave(() => {
    currentActiveAccordion.value = null
  })
</script>
