<script setup lang="ts">
import {onMounted, ref, watch} from "vue";
import {useRoute, useRouter} from "vue-router";

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
const router = useRouter();
const route = useRoute();

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
</script>

<template>
  <div class='grid tab-menu mt-5'>
    <div class='col-12'>
      <TabMenu
          class="mb-4"
          v-model:activeIndex="active"
          :model="productsItems">
        <template #item="{ item }">
          <router-link
              v-if="item.route"
              v-slot="routerProps"
              :to="item.route"
              custom
          >
            <a
                :href="routerProps.href"
                v-bind="item.action"
                @click="($event) => routerProps.navigate($event)"
                @keydown.enter.space="($event) => routerProps.navigate($event)"
            >
              <span v-bind="item.icon" />
              <span v-bind="item.label">{{ item.label }}</span>
            </a>
          </router-link>
        </template>
      </TabMenu>
      <router-view />
    </div>
  </div>
</template>

<style scoped>

</style>