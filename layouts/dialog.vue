<script setup lang="ts">
import { useThemeStore } from '~/stores'
const themeStore = useThemeStore()
const router = useRouter()
const productsItems = ref([
  {
    label: 'Наборы',
    route: '/sets'
  },
  {
    label: 'Суши',
    route: '/sushi'
  },
  {
    label: 'Роллы',
    route: '/rolls'
  },
  {
    label: 'Теплые Роллы',
    route: '/warmRolls'
  },
  {
    label: 'Маки',
    route: '/maki'
  },
  {
    label: 'Салаты',
    route: '/salads'
  },
  {
    label: 'Напитки',
    route: '/drinks'
  },
  {
    label: 'Соусы',
    route: '/sauces'
  },
]);
// ...........
const visible = ref(false);
const visibleInfo = ref(false)
const visibleMap = ref(false)


const openDialog = () => {
  visibleInfo.value = true
}
const openMap = () => {
  visibleMap.value = true
}

const openPosition = () => {
  visible.value = true;
}
</script>
<template>
  <div>
    <Link rel="stylesheet" :href="themeStore.link" />
    <header class="sticky top-0 bg-white z-100">
      <div class='container'>
        <div class='flex justify-content-between align-items-center py-3 mb-4'>
          <div class='logo'>
            <img class='w-full' src='https://takamura-eats.ru/custom/my/img/logo22.png' alt=''>
          </div>
          <ul class='menu'>
            <li class='menu__item'>
              <a class='menu-link' href='tel:+7(499)1123817' style='letter-spacing: 0.72px;'>+7(499)112-38-17</a>
            </li>
            <li class='menu__item'>
              <button class='menu-link border-1 border-circle p-1 bg-transparent cursor-pointer' @click="openDialog()" severity="help">
                <i class='pi pi-info text-sm'></i>
              </button>
              <Dialog class="dialog-menu dialog-menu--full" v-model:visible="visibleInfo" :style="{ width: '100vw' }" position="top" :modal="true" :draggable="false">
                <template #header>
                  <img src="https://takamura-eats.ru/custom/my/img/logo22.png" alt="">
                </template>
                <div class="flex flex-column align-items-center w-full">
                  <h1 class="dialog-caption dialog-caption--big-text text-center">ИНФОРМАЦИЯ О ДОСТАВКЕ</h1>
                  <p class="dialog-caption w-full sm:w-6 text-center line-height-2">Мы принимаем заказы с 10.00 до 22.30
                    Доставляем заказы с 11.00 до 23.20</p>
                </div>
                <h1 class="dialog-caption">Доставка осуществляется по зонам:</h1>
                <div class="grid">
                  <div class="col-12 sm:col-6 md:col-4">
                    <div class="card">
                      <h1 class="dialog-caption">
                        <span class="border-bottom-1">СЕРАЯ ЗОНА</span>
                      </h1>
                      <p class="dialog-description">Доставка от 700 р.</p>
                      <p class="dialog-description">Способы оплаты: картой на сайте,картой курьеру, наличными.</p>
                      <p class="dialog-description">Время доставки 1-1,2 часа.</p>
                    </div>
                  </div>
                  <div class="col-12 sm:col-6 md:col-4">
                    <div class="card">
                      <h1 class="dialog-caption">
                        <span class="border-bottom-1">ГОЛУБАЯ ЗОНА</span>
                      </h1>
                      <p class="dialog-description">Доставка от 1200 р.</p>
                      <p class="dialog-description">Оплата картой на сайте</p>
                      <p class="dialog-description">Время доставки 1-1,3 часа.</p>
                    </div>
                  </div>
                  <div class="col-12 sm:col-6 md:col-4">
                    <div class="card">
                      <h1 class="dialog-caption">
                        <span class="border-bottom-1">СИНЯЯ ЗОНА</span>
                      </h1>
                      <p class="dialog-description">Доставка от 2000 р.</p>
                      <p class="dialog-description">Оплата картой на сайте</p>
                      <p class="dialog-description">Время доставки 1-2 часа.</p>
                    </div>
                  </div>
                  <div class="col-12 sm:col-6 md:col-4">
                    <div class="card">
                      <h1 class="dialog-caption">
                        <span class="border-bottom-1">РОЗОВАЯ ЗОНА</span>
                      </h1>
                      <p class="dialog-description">Доставка от 700 р.</p>
                      <p class="dialog-description">Оплата картой на сайте</p>
                      <p class="dialog-description">Время доставки 1-1,2 часа.</p>
                    </div>
                  </div>
                  <div class="col-12 sm:col-6 md:col-4">
                    <div class="card">
                      <h1 class="dialog-caption">
                        <span class="border-bottom-1">ЗЕЛЕНАЯ ЗОНА</span>
                      </h1>
                      <p class="dialog-description">Доставка от 1800 р.</p>
                      <p class="dialog-description">Оплата картой на сайте</p>
                      <p class="dialog-description">Время доставки 1-1,4 часа.</p>
                    </div>
                  </div>
                  <div class="col-12 sm:col-6 md:col-4">
                    <div class="card">
                      <h1 class="dialog-caption">
                        <span class="border-bottom-1">КРАСНАЯ ЗОНА</span>
                      </h1>
                      <p class="dialog-description">Доставка от 2500 р.</p>
                      <p class="dialog-description">Оплата картой на сайте</p>
                      <p class="dialog-description">Время доставки 1-2 часа.</p>
                    </div>
                  </div>
                </div>
                <button class="mx-auto dialog-button" @click="openMap()">Посмотреть на карте</button>
                <p class="contacts-default mx-auto">
                  <a href="tel:+7(499)1123817">+7 (499) 112-38-17</a>
                </p>
                <p class="contacts-default mx-auto">
                  <a href="mailto:feedback@takamura-eats.ru">feedback@takamura-eats.ru</a>
                </p>
              </Dialog>
            </li>
            <li class='menu__item'>
              <button class='menu-link bg-transparent border-none cursor-pointer' @click="openMap()">
                <i class='pi pi-map text-xl'></i>
              </button>
              <Dialog class="dialog-menu dialog-menu--full" v-model:visible="visibleMap" :style="{ width: '100vw' }" position="top" :modal="true" :draggable="false">
                <template #header>
                  <img  src="https://takamura-eats.ru/custom/my/img/logo22.png" alt="">
                </template>
                <div class="flex flex-column align-items-center w-full">
                  <h1 class="dialog-caption dialog-caption--big-text">ИНФОРМАЦИЯ О ДОСТАВКЕ</h1>
                  <p class="dialog-caption w-full sm:w-6 text-center line-height-2 mb-5">Мы принимаем заказы с 10.00 до 22.30
                    Доставляем заказы с 11.00 до 23.20</p>
                </div>
                <div>
                  <iframe src="https://yandex.ru/map-widget/v1/?um=constructor%3A759b6fceb84b20d842bb3ebef1ee8694f7c066ee7fa7a5e87d9d719aada7e9b6&amp;source=constructor" width="100%" height="400" frameborder="0"></iframe>
                </div>
                <button class="dialog-button" @click="openDialog()">Посмотреть списком</button>
                <p class="contacts-default mx-auto">
                  <a href="tel:+7(499)1123817">+7 (499) 112-38-17</a>
                </p>
                <p class="contacts-default mx-auto">
                  <a href="mailto:feedback@takamura-eats.ru">feedback@takamura-eats.ru</a>
                </p>
              </Dialog>
            </li>
            <li class='menu__item'>
              <router-link class='menu-link' to='/cart'><i class='pi pi-shopping-cart text-xl'></i></router-link>
            </li>
            <li>
              <button class='burger' @click="openPosition()" severity="help" >
                <div class='burger-item'></div>
                <div class='burger-item'></div>
                <div class='burger-item'></div>
              </button>
              <div >
                <Dialog class="dialog-menu" v-model:visible="visible" :style="{ width: '50vw' }" position="right" :modal="true" :draggable="false">
                  <template #header>
                    <img src="https://takamura-eats.ru/custom/my/img/logo22.png" alt="">
                  </template>
                  <div class="flex flex-column">
                    <NuxtLink to="" class="font-normal product-caption mb-0 cursor-pointer">ПРОГРАММА ЛОЯЛЬНОСТИ</NuxtLink>
                    <NuxtLink to="" class="font-normal product-caption mb-0 cursor-pointer">АКЦИИ</NuxtLink>
                    <NuxtLink to="/" class="font-normal product-caption mb-0 cursor-pointer">МЕНЮ</NuxtLink>
                    <ul>
                      <li @click="router.push('/sets');">
                        <NuxtLink class="cursor-pointer product-caption font-light underline">НАБОРЫ</NuxtLink>
                      </li>
                      <li @click="router.push('/sushi')">
                        <NuxtLink class="cursor-pointer product-caption font-light underline">СУШИ</NuxtLink>
                      </li>
                      <li @click="router.push('/rolls')">
                        <NuxtLink class="cursor-pointer product-caption font-light underline">РОЛЛЫ</NuxtLink>
                      </li>
                      <li @click="router.push('/warmRolls')">
                        <NuxtLink class="cursor-pointer product-caption font-light underline">ТЕПЛЫЕ РОЛЛЫ</NuxtLink>
                      </li>
                      <li @click="router.push('/maki')">
                        <NuxtLink class="cursor-pointer product-caption font-light underline">МАКИ</NuxtLink>
                      </li>
                      <li @click="router.push('/salads')">
                        <NuxtLink class="cursor-pointer product-caption font-light underline">САЛАТЫ</NuxtLink>
                      </li>
                      <li @click="router.push('/drinks')">
                        <NuxtLink class="cursor-pointer product-caption font-light underline">НАПИТКИ</NuxtLink>
                      </li>
                      <li @click="router.push('/sauces')">
                        <NuxtLink  class="cursor-pointer product-caption font-light underline">СОУСЫ</NuxtLink>
                      </li>
                    </ul>
                    <NuxtLink to="/contacts" class="font-normal product-caption mb-0 cursor-pointer">КОНТАКТЫ</NuxtLink>
                  </div>
                </Dialog>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </header>
    <slot />
    <footer class="mt-8">
      <div class="container">
        <p class="contacts-default">
          <a href="tel:+7(499)1123817">+7 (499) 112-38-17</a>
        </p>
        <p class="contacts-default">
          <a href="mailto:feedback@takamura-eats.ru">feedback@takamura-eats.ru</a>
        </p>
        <p class="contacts-default">сотрудничество</p>
      </div>
    </footer>
  </div>
</template>
<style scoped>
.contacts-default{
  font-weight: 300;
  line-height: 31px;
  margin-bottom: 0;
  font-family: 'Victor Mono', monospace;
  font-size: 22px;
  color: #1F1E23;

}
</style>