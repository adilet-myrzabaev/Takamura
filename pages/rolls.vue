<script lang='ts' setup>
import { ref } from 'vue';
const products = ref([
  {
    id: 1,
    img: 'https://takamura-eats.ru/userfls/shop/small/1629_filadelfiya-.jpg',
    caption: 'ФИЛАДЕЛЬФИЯ',
    description: 'Лосось, сливочный сыр',
    weight: '130',
    portion: '4',
    kBJU: '209/8/12/16',
    price: '280'
  },
  {
    id: 2,
    img: 'https://takamura-eats.ru/userfls/shop/small/1629_filadelfiya-.jpg',
    caption: 'ФИЛАДЕЛЬФИЯ',
    description: 'Лосось, сливочный сыр',
    weight: '130',
    portion: '4',
    kBJU: '209/8/12/16',
    price: '280'
  },
  {
    id: 3,
    img: 'https://takamura-eats.ru/userfls/shop/small/1629_filadelfiya-.jpg',
    caption: 'ФИЛАДЕЛЬФИЯ',
    description: 'Лосось, сливочный сыр',
    weight: '130',
    portion: '4',
    kBJU: '209/8/12/16',
    price: '280'
  },
  {
    id: 4,
    img: 'https://takamura-eats.ru/userfls/shop/small/1629_filadelfiya-.jpg',
    caption: 'ФИЛАДЕЛЬФИЯ',
    description: 'Лосось, сливочный сыр',
    weight: '130',
    portion: '4',
    kBJU: '209/8/12/16',
    price: '280'
  }
])
const count = ref(0)

const  countNum = () => {
  count.value++
}
const  minusNum = () => {
  count.value--
}
</script>

<template>
  <div>
    <div class='grid product-parent'>
      <Card v-for='product in products' class='col-12 sm:col-6 md:col-4 lg:col-3'>
        <template #header>
          <img class="w-full" :src='product.img' :alt='product.caption'>
        </template>
        <template #content>
          <h5 class='product-caption'>{{product.caption}}</h5>
          <p class='product-description'>{{product.description}}</p>
          <p class='product-description'>Вес: {{product.weight}} г</p>
          <p class='product-description' v-if='product.kBJU'>КБЖУ: {{product.kBJU}}</p>
          <p class='product-description'>Порция: {{product.portion}} шт</p>
        </template>
        <template #footer>
          <div class='flex align-items-center justify-content-between'>
            <p class='text-xl product-caption mb-0'>{{product.price}}. -</p>
            <div class='flex align-items-center'>
              <button v-if='count>0' class='border-1 mr-3 btn-count' @click='minusNum'><i class='pi pi-minus p-1'></i></button>
              <span v-if='count'>{{ count }}</span>
              <button class='border-1 ml-3 btn-count' @click='countNum'><i class='pi pi-plus p-1'></i></button>
            </div>
          </div>
        </template>
      </Card>
    </div>
  </div>
</template>