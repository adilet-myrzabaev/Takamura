<script lang='ts' setup>
const products = ref([
  {
    id: 0,
    img: '',
    caption: '',
    description: '',
    weight: '',
    portion: '',
    kBJU: '',
    price: ''
  },
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
      <h1>Напитки нет</h1>
      <Card v-for='product in products' class='col-12 sm:col-6 md:col-4 lg:col-3'>
        <template #header>
          <img class="w-full" :src='product.img' :alt='product.caption'>
        </template>
        <template #content>
          <h5 class='product-caption'>{{product.caption}}</h5>
          <p class='product-description'>{{product.description}}</p>
          <p class='product-description' v-if="product.weight">Вес: {{product.weight}} г</p>
          <p class='product-description' v-if='product.kBJU'>КБЖУ: {{product.kBJU}}</p>
          <p class='product-description' v-if="product.portion">Порция: {{product.portion}} шт</p>
        </template>
        <template #footer>
          <div class='flex align-items-center justify-content-between'>
            <p class='text-xl product-caption mb-0' v-if="product.price">{{product.price}}. -</p>
            <div class='flex align-items-center'>
              <button v-if='count>0' class='border-1 mr-3 btn-count' @click='minusNum'><i class='pi pi-minus p-1'></i></button>
              <span v-if='count'>{{ count }}</span>
              <button v-if="product.caption" class='border-1 ml-3 btn-count' @click='countNum'><i class='pi pi-plus p-1'></i></button>
            </div>
          </div>
        </template>
      </Card>
    </div>
  </div>
</template>