<script setup lang="ts">
import {useAuthStore, useIsLoadingStore} from '~/store/auth.store';

const router = useRouter()

const isLoadingStore = useIsLoadingStore()
const authStore = useAuthStore()

  const logout = async () => {
    isLoadingStore.set(true)
    await account.deleteSession('current')
    authStore.clear()

    await router.push('/login')

    isLoadingStore.set(false)
  }
</script>

<template>
  <aside class="px-5 py-8 bg-sidebar h-full relative w-full">
    <NuxtLink to="/" class="mb-10 block">
      <NuxtImg src="/logo.svg" width="140px" class="mx-auto"/>
    </NuxtLink>
    <button @click="logout" class="absolute top-2 right-3 transition-colors hover:text-primary">
      <Icon name="line-md:logout" size="20"/>
    </button>
    <LayoutMenu/>
  </aside>
</template>

<style scoped>

</style>