<script setup lang='ts'>
import { ref, onMounted, watch } from "vue";
import { useRoute, useRouter } from 'vue-router';
import { useThemeStore } from '~/stores'

const themeStore = useThemeStore()

const productsCarousel = ref([
  {
    id: 1,
    img: 'https://takamura-eats.ru/userfls/bs/1_42.jpg',
    caption: 'Роллы Takamura',
    description: 'Лосось, тунец, тигровые креветки и морской гребешок в наших роллах приправлены исключительно натуральными соусами.',
  },
  {
    id: 2,
    img: 'https://takamura-eats.ru/userfls/bs/3-1_41.jpg',
    caption: 'Роллы Takamura',
    description: 'Лосось, тунец, тигровые креветки и морской гребешок в наших роллах приправлены исключительно натуральными соусами.',
  },
  {
    id: 3,
    img: 'https://takamura-eats.ru/userfls/bs/2_43.jpg',
    caption: 'Роллы Takamura',
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

watch(route, () => {
      active.value = productsItems.value.findIndex((item) => route.path === router.resolve(item.route).path);
    },
    { immediate: true }
);


</script>

<template>
  <div>
    <Link rel="stylesheet" :href="themeStore.link" />
    <header>
      <div class='container'>
        <div class='flex justify-content-between align-items-center py-3'>
          <div class='logo'>
            <img class='w-full' src='https://takamura-eats.ru/custom/my/img/logo22.png' alt=''>
          </div>
          <ul class='menu'>
            <li class='menu__item'>
              <a class='menu-link' href='tel:+7(499)1123817' style='letter-spacing: 0.72px;'>+7(499)112-38-17</a>
            </li>
            <li class='menu__item'>
              <router-link class='menu-link border-1 border-circle p-1' to=''><i class='pi pi-info text-sm'></i></router-link>
            </li>
            <li class='menu__item'>
              <router-link class='menu-link' to=''><i class='pi pi-map text-xl'></i></router-link>
            </li>
            <li class='menu__item'>
              <router-link class='menu-link' to=''><i class='pi pi-shopping-cart text-xl'></i></router-link>
            </li>
            <li>
              <div class='burger'>
                <div class='burger-item'></div>
                <div class='burger-item'></div>
                <div class='burger-item'></div>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </header>
    <section>
      <div class='container'>
        <div class='grid carousel-parent'>
          <div class='col-12'>
            <Carousel :value="productsCarousel" :numVisible="1" :numScroll="1" :responsiveOptions="responsiveOptions" circular :autoplayInterval="6000">
              <template #item="slotProps">
                <div class="flex border-1 surface-border border-round m-2 text-center py-5 px-3">
                  <div class="mb-3">
                    <img :src="slotProps.data.img" :alt="slotProps.data.name" class="h-full w-10 shadow-3" />
                  </div>
                  <div class="flex flex-column justify-content-center relative ml-3">
                    <h4 class="mb-1 text-left">{{ slotProps.data.caption }}</h4>
                    <h6 class="mt-0 mb-3 text-left">{{ slotProps.data.description }}</h6>
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

            </TabMenu>
            <slot />
          </div>
        </div>
      </div>
    </section>

  </div>
</template>
