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
                  <h1>ИНФОРМАЦИЯ О ДОСТАВКЕ</h1>
                  <p>Мы принимаем заказы с 10.00 до 22.30
                    Доставляем заказы с 11.00 до 23.20</p>
                </div>
                <h1>Доставка осуществляется по зонам:</h1>
                <div class="grid">
                  <div class="col-4">
                    <div class="card">
                      <h1>СЕРАЯ ЗОНА</h1>
                      <p>Доставка от 700 р.</p>
                      <p>Способы оплаты: картой на сайте,картой курьеру, наличными.</p>
                      <p>Время доставки 1-1,2 часа.</p>
                    </div>
                  </div>
                  <div class="col-4">
                    <div class="card">
                      <h1>ГОЛУБАЯ ЗОНА</h1>
                      <p>Доставка от 1200 р.</p>
                      <p>Оплата картой на сайте</p>
                      <p>Время доставки 1-1,3 часа.</p>
                    </div>
                  </div>
                  <div class="col-4">
                    <div class="card">
                      <h1>СИНЯЯ ЗОНА</h1>
                      <p>Доставка от 2000 р.</p>
                      <p>Оплата картой на сайте</p>
                      <p>Время доставки 1-2 часа.</p>
                    </div>
                  </div>
                  <div class="col-4">
                    <div class="card">
                      <h1>РОЗОВАЯ ЗОНА</h1>
                      <p>Доставка от 700 р.</p>
                      <p>Оплата картой на сайте</p>
                      <p>Время доставки 1-1,2 часа.</p>
                    </div>
                  </div>
                  <div class="col-4">
                    <div class="card">
                      <h1>ЗЕЛЕНАЯ ЗОНА</h1>
                      <p>Доставка от 1800 р.</p>
                      <p>Оплата картой на сайте</p>
                      <p>Время доставки 1-1,4 часа.</p>
                    </div>
                  </div>
                  <div class="col-4">
                    <div class="card">
                      <h1>КРАСНАЯ ЗОНА</h1>
                      <p>Доставка от 2500 р.</p>
                      <p>Оплата картой на сайте</p>
                      <p>Время доставки 1-2 часа.</p>
                    </div>
                  </div>
                </div>
                <button class="mx-auto">Посмотреть на карте</button>
                <p>
                  <router-link to="tel:+7(499)1123817">+7 (499) 112-38-17</router-link>
                </p>
                <p>
                  <router-link to="mailto:feedback@takamura-eats.ru">feedback@takamura-eats.ru</router-link>
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
                  <h1>ИНФОРМАЦИЯ О ДОСТАВКЕ</h1>
                  <p>Мы принимаем заказы с 10.00 до 22.30
                    Доставляем заказы с 11.00 до 23.20</p>
                </div>
                <div>
                  <iframe src="https://yandex.ru/map-widget/v1/?um=constructor%3A759b6fceb84b20d842bb3ebef1ee8694f7c066ee7fa7a5e87d9d719aada7e9b6&amp;source=constructor" width="100%" height="400" frameborder="0"></iframe>
                </div>
                <button class="mx-auto">Посмотреть на карте</button>
                <p>
                  <router-link to="tel:+7(499)1123817">+7 (499) 112-38-17</router-link>
                </p>
                <p>
                  <router-link to="mailto:feedback@takamura-eats.ru">feedback@takamura-eats.ru</router-link>
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
                  <p class="font-normal product-caption mb-0 cursor-pointer">ПРОГРАММА ЛОЯЛЬНОСТИ</p>
                  <p class="font-normal product-caption mb-0 cursor-pointer">АКЦИИ</p>
                  <p class="font-normal product-caption mb-0 cursor-pointer">МЕНЮ</p>
                  <ul v-for="product in productsItems">
                    <li class="cursor-pointer product-caption font-light underline" @click="router.push(`${product.route}`); visible=false">
                      {{ product.label}}
                    </li>
                  </ul>
                  <p class="font-normal product-caption mb-0 cursor-pointer">КОНТАКТЫ</p>
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
                    <div class="absolute bottom-0 right-0 flex align-items-center">
                      <button class=' pr-3 border-none bg-transparent'>что ещё </button>
                      <i class='pi pi-angle-right'></i>
                    </div>
                  </div>

                </div>
              </template>
            </Carousel>
          </div>
        </div>
        <div class='grid tab-menu mt-5'>
          <div class='col-12'>
            <TabMenu v-model:activeIndex="active" :model="productsItems">
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
      </div>
    </section>

  </div>
</template>
