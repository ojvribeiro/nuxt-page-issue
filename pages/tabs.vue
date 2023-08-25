<template>
  <div class="py-10">
    <Container>
      <div class="space-y-8 rounded-2xl border border-gray-300">
        <div class="bg-gray-50/50">
          <Tab>
            <TabItem
              :active="route.path.match('/tabs/tab1') !== null"
              @click="changeTab('tab1')"
            >
              Tab 1
            </TabItem>

            <TabItem
              :active="route.path.match('/tabs/tab2') !== null"
              @click="changeTab('tab2')"
            >
              Tab 2
            </TabItem>

            <TabItem
              :active="route.path.match('/tabs/tab3') !== null"
              @click="changeTab('tab3/subtab1')"
            >
              Tab 3
            </TabItem>
          </Tab>
        </div>

        <!-- `/pages/tabs` -->
        <div class="px-4 pb-4">
          <NuxtPage />
        </div>
      </div>
    </Container>
  </div>
</template>

<script setup lang="ts">
  const route = useRoute()

  function changeTab(path: string) {
    if (route.path.match(`/tabs/${path}`)) {
      return
    }

    navigateTo(`/tabs/${path}`)
  }

  if (route.path === '/tabs') {
    navigateTo('/tabs/tab1', { redirectCode: 301 })
  }
</script>
