<script setup lang='ts'>
import { ref, onMounted, watch } from "vue";
import { useRoute, useRouter } from 'vue-router';
import { useThemeStore } from '~/stores'

const themeStore = useThemeStore()

const productsCarousel = ref([
  {
    id: 1,
    img: 'https://takamura-eats.ru/userfls/bs/1_42.jpg',
    caption: 'РОЛЛЫ TAKAMURA',
    description: 'Лосось, тунец, тигровые креветки и морской гребешок в наших роллах приправлены исключительно натуральными соусами.',
  },
  {
    id: 2,
    img: 'https://takamura-eats.ru/userfls/bs/3-1_41.jpg',
    caption: 'РОЛЛЫ TAKAMURA',
    description: 'Лосось, тунец, тигровые креветки и морской гребешок в наших роллах приправлены исключительно натуральными соусами.',
  },
  {
    id: 3,
    img: 'https://takamura-eats.ru/userfls/bs/2_43.jpg',
    caption: 'РОЛЛЫ TAKAMURA',
    description: 'Лосось, тунец, тигровые креветки и морской гребешок в наших роллах приправлены исключительно натуральными соусами.',
  },
]);
const responsiveOptions = ref([
  {
    breakpoint: '1199px',
    numVisible: 1,
    numScroll: 1
  },
  {
    breakpoint: '991px',
    numVisible: 1,
    numScroll: 1
  },
  {
    breakpoint: '767px',
    numVisible: 1,
    numScroll: 1
  }
]);


const router = useRouter();
const route = useRoute();

const active = ref(0);
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

onMounted(() => {
  active.value = productsItems.value.findIndex((item) => route.path === router.resolve(item.route).path);
})

watch(
    route,
    () => {
      active.value = productsItems.value.findIndex((item) => route.path === router.resolve(item.route).path);
    },
    { immediate: true }
);
// /////////DIALOG//////////////

const visible = ref(false);
const visibleInfo = ref(false)
const visibleMap = ref(false)


const openDialog = () => {
  visibleInfo.value = true
  visibleMap.value = false
}
const openMap = () => {
  visibleMap.value = true
  visibleInfo.value = false
}

const openPosition = () => {
  visible.value = true;
}
// /////////////////////count/////////
const count = ref(0)

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
                <p class="contacts-default text-center">
                  <a href="tel:+7(499)1123817">+7 (499) 112-38-17</a>
                </p>
                <p class="contacts-default text-center">
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
                <p class="contacts-default text-center">
                  <a href="tel:+7(499)1123817">+7 (499) 112-38-17</a>
                </p>
                <p class="contacts-default text-center">
                  <a href="mailto:feedback@takamura-eats.ru">feedback@takamura-eats.ru</a>
                </p>
              </Dialog>
            </li>
            <li class='menu__item'>
              <router-link class='menu-link relative' to='/cart'>
                <i class='pi pi-shopping-cart text-xl'></i>
                <span class="absolute top-50 left-100 text-sm font-light font-mono">{{ count }}</span>
              </router-link>
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
                  <router-link to="" class="font-normal product-caption mb-0 cursor-pointer">ПРОГРАММА ЛОЯЛЬНОСТИ</router-link>
                  <router-link to="" class="font-normal product-caption mb-0 cursor-pointer">АКЦИИ</router-link>
                  <router-link to="/sets" class="font-normal product-caption mb-0 cursor-pointer">МЕНЮ</router-link>
                  <ul v-for="product in productsItems">
                    <li class="cursor-pointer product-caption font-light underline" @click="router.push(`${product.route}`); visible=false">
                      {{ product.label}}
                    </li>
                  </ul>
                  <router-link to="/contacts" class="font-normal product-caption mb-0 cursor-pointer">КОНТАКТЫ</router-link>
                </Dialog>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </header>
    <section>
      <div class='container'>
        <div class='grid carousel-parent' style="margin-top: 40px;">
          <div class='col-12'>
            <Carousel :value="productsCarousel" :numVisible="1" :numScroll="1" :responsiveOptions="responsiveOptions" circular :autoplayInterval="6000">
              <template #item="slotProps">
                <div class="flex border-1 surface-border border-round-2xl m-2 text-center py-5 px-3">
                  <div class="mb-3">
                    <img :src="slotProps.data.img" :alt="slotProps.data.name" class="h-full w-10 shadow-3 border-round-2xl" />
                  </div>
                  <div class="flex flex-column justify-content-center relative ml-3">
                    <h4 class="mb-1 text-left carousel-caption font-semibold">{{ slotProps.data.caption }}</h4>
                    <h6 class="mt-0 mb-3 text-left carousel-description">{{ slotProps.data.description }}</h6>
                  </div>

                </div>
              </template>
            </Carousel>
          </div>
        </div>
        <div class='grid tab-menu mt-5'>
          <div class='col-12'>
            <TabMenu class="mb-4" v-model:activeIndex="active" :model="productsItems">
              <template #item="{ item }">
                <router-link v-if="item.route" v-slot="routerProps" :to="item.route" custom>
                  <a :href="routerProps.href" v-bind="item.action" @click="($event) => routerProps.navigate($event)" @keydown.enter.space="($event) => routerProps.navigate($event)">
                    <span v-bind="item.icon" />
                    <span v-bind="item.label">{{ item.label }}</span>
                  </a>
                </router-link>
              </template>
            </TabMenu>
            <router-view />
          </div>
        </div>
        <footer class="mt-8">
          <div class="container">
            <p class="contacts-default">
              <a href="tel:+7(499)1123817">+7 (499) 112-38-17</a>
            </p>
            <p class="contacts-default">
              <a href="mailto:feedback@takamura-eats.ru">feedback@takamura-eats.ru</a>
            </p>
            <p class="contacts-default">
              <a href="#">сотрудничество</a>
            </p>
          </div>
        </footer>
      </div>
    </section>

  </div>
</template>
