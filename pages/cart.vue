<template>
<div class="container">
  <div class="h-screen flex flex-column justify-content-center align-items-center">
    <h1 class="dialog-caption text-6xl text-center">Корзина пуста</h1>
    <button class="dialog-button" @click="router.push('/sets')">Перейти к покупкам</button>
  </div>
</div>
</template>
<script lang="ts" setup>
definePageMeta({
  layout: 'dialog'
})
const router = useRouter()
</script>