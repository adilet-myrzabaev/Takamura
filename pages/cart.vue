<template>
<div class="container">
<!--  <div class="h-screen flex flex-column justify-content-center align-items-center">-->
<!--    <h1 class="dialog-caption text-6xl text-center">Корзина пуста</h1>-->
<!--    <NuxtLink class="dialog-button" to="/">Перейти к покупкам</NuxtLink>-->
<!--  </div>-->
  <div class="grid">
    <div class="col-6 border-right-1 border-black-alpha-80 pr-5">
      <div class="grid">
        <div class="col-12">
          <CascadeSelect class="w-full border-none border-bottom-1 border-noround shadow-noneзтзть" v-model="selectedCity" :options="countries" optionLabel="cname" optionGroupLabel="name"
                         :optionGroupChildren="['states', 'cities']" style="min-width: 14rem" placeholder="Select a City">
            <template #option="slotProps">
              <div class="flex align-items-center">
                <img v-if="slotProps.option.states" :alt="slotProps.option.name" src="https://primefaces.org/cdn/primevue/images/flag/flag_placeholder.png" :class="`flag flag-${slotProps.option.code.toLowerCase()} mr-2`" style="width: 18px"  />
                <i v-if="slotProps.option.cities" class="pi pi-compass mr-2"></i>
                <i v-if="slotProps.option.cname" class="pi pi-map-marker mr-2"></i>
                <span>{{ slotProps.option.cname || slotProps.option.name }}</span>
              </div>
            </template>
          </CascadeSelect>
        </div>
        <div class="col-12">
          <InputText class="w-full border-noround border-none shadow-none border-bottom-1 border-black-alpha-80" placeholder="Ваше имя" />
        </div>
        <div class="col-6">
          <InputText class="w-full border-noround border-none shadow-none border-bottom-1 border-black-alpha-80" placeholder="Телефон" />
        </div>
        <div class="col-6">
          <InputText class="w-full border-noround border-none shadow-none border-bottom-1 border-black-alpha-80" placeholder="Email" />
        </div>
        <div class="col-3">
          <InputText class="w-full border-noround border-none shadow-none border-bottom-1 border-black-alpha-80" placeholder="Приборы" />
        </div>
        <div class="col-9">
          <InputText class="w-full border-noround border-none shadow-none border-bottom-1 border-black-alpha-80" placeholder="Комментарий" />
        </div>
        <div class="col-4">
          <InputText class="w-full border-noround border-none shadow-none border-bottom-1 border-black-alpha-80" placeholder="Промокод" />
        </div>
        <div class="col-4">
          <InputText class="w-full border-noround border-none shadow-none border-bottom-1 border-black-alpha-80" placeholder="Бонусы" />
        </div>
        <div class="col-4">
          <button class="bg-transparent border-black-alpha-80 border-1 border-round-md p-2" >Списать бонусы</button>

        </div>
        <div class="col-12">
          <span class="pi pi-clock"></span>
          <InputText class=" w-full border-noround border-none shadow-none border-bottom-1 border-black-alpha-80" placeholder="Заказ на ближайшее время" />
        </div>
        <div class="col-12">
          <i class="pi pi-credit-card"></i>
          <InputText class="w-full border-noround border-none shadow-none border-bottom-1 border-black-alpha-80" placeholder="Картой на сайте" />
        </div>
      </div>
    </div>
    <div class="col-6">
    </div>
  </div>
</div>
</template>
<script lang="ts" setup>
definePageMeta({
  layout: 'dialog'
})
const selectedCity = ref();
const countries = ref([
  {
    cname: 'Курьер',
    code: 'ku'
  },
  {
    cname: 'Самовывоз (Россошанский пр-д 3, ТЦ Прага)',
    code: 'rc'
  },
  {
    cname: 'Самовывоз (Шереметьевская ул. 6 кор. 1, ТРЦ Райкин Плаза)',
    code: 'sh'
  },
  {
    cname: 'Самовывоз (Произвеодственная 12к1, Порт Пивных Дегустаторов)',
    code: 'pr'
  }
]);
</script>