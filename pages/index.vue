<script setup lang='ts'>
import { ref } from 'vue';

const count = ref(0)
const productsSets = ref([
  {
    id: 1,
    img: 'https://takamura-eats.ru/userfls/shop/small/1221_lux.jpg',
    caption: 'LUX',
    description: 'Калифорния с камчатским крабом и манго, Дракон с креветкой, Филадельфия люкс, Манго-авокадо',
    weight: '902',
    portion: '32',
    kBJU: '',
    price: '2250'
  },
  {
    id: 2,
    img: 'https://takamura-eats.ru/userfls/shop/small/1221_lux.jpg',
    caption: 'LUX',
    description: 'Калифорния с камчатским крабом и манго, Дракон с креветкой, Филадельфия люкс, Манго-авокадо',
    weight: '902',
    portion: '32',
    kBJU: '',
    price: '2250'
  },
  {
    id: 3,
    img: 'https://takamura-eats.ru/userfls/shop/small/1221_lux.jpg',
    caption: 'LUX',
    description: 'Калифорния с камчатским крабом и манго, Дракон с креветкой, Филадельфия люкс, Манго-авокадо',
    weight: '902',
    portion: '32',
    kBJU: '',
    price: '2250'
  },
  {
    id: 4,
    img: 'https://takamura-eats.ru/userfls/shop/small/1221_lux.jpg',
    caption: 'LUX',
    description: 'Калифорния с камчатским крабом и манго, Дракон с креветкой, Филадельфия люкс, Манго-авокадо',
    weight: '902',
    portion: '32',
    kBJU: '',
    price: '2250'
  }
])
const  countNum = () => {
  count.value++
}
const  minusNum = () => {
  count.value--
}
</script>

<template>
  <div class="container">
    <div class="grid">
      <div class="col-12">
        <h1>Наборы</h1>
        <div class='grid product-parent'>
          <Card v-for='product in productsSets' class='col-6 md:col-4 lg:col-3 '>
            <template #header>
              <img class="w-full" :src='product.img' :alt='product.caption'>
            </template>
            <template #content>
              <h4 class='product-caption'>{{product.caption}}</h4>
              <p class='product-description'>{{product.description}}</p>
              <p class='product-description'>Вес: {{product.weight}} г</p>
              <p class='product-description' v-if='product.kBJU'>КБЖУ: {{product.kBJU}}</p>
              <p class='product-description'>Порция: {{product.portion}} шт</p>
            </template>
            <template #footer>
              <div class='flex align-items-center justify-content-between'>
                <p class='text-xl product-caption mb-0'>{{product.price}}. -</p>
                <div class='flex align-items-center'>
                  <button v-if='count>0' class='border-1 mr-3' style='border-radius: 7px' @click='minusNum'><i class='pi pi-minus p-1'></i></button>
                  <span v-if='count'>{{ count }}</span>
                  <button class='border-1 ml-3' style='border-radius: 7px' @click='countNum'><i class='pi pi-plus p-1'></i></button>
                </div>
              </div>
            </template>
          </Card>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
