<template>
  <div>
    <div class="container">
      <div class="grid">
        <div class="col-6">
          <div class="grid">
            <div class="col-12">
              <div class="card">
                <h1 class="dialog-caption">
                  <span class="border-bottom-1">
                    TAKAMURA В МАРЬИНОЙ РОЩЕ
                  </span>
                </h1>
                <p class="dialog-description">ТРЦ Райкин Плаза</p>
                <p class="dialog-description">Шереметьевская ул. 6к1</p>
                <p class="dialog-description">Ежедневно с 10.00 до 23.00</p>
              </div>
            </div>
            <div class="col-12">
              <div class="card">
                <h1 class="dialog-caption">
                  <span class="border-bottom-1">
                    TAKAMURA В СОЛНЦЕВО
                  </span>
                </h1>
                <p class="dialog-description">Порт Пивных Дегустаторов</p>
                <p class="dialog-description">Производственная ул. 12к1</p>
                <p class="dialog-description">Ежедневно с 11.00 до 23.00</p>
              </div>
            </div>
            <div class="col-12">
              <div class="card">
                <h1 class="dialog-caption">
                  <span class="border-bottom-1">
                    TAKAMURA В ЧЕРТАНОВО
                  </span>
                </h1>
                <p class="dialog-description">ТЦ Прага</p>
                <p class="dialog-description">Россошанский пр-д 3</p>
                <p class="dialog-description">Ежедневно с 10.00 до 23.00</p>
              </div>
            </div>
          </div>
        </div>
        <div class="col-6">
          <iframe src="https://yandex.ru/map-widget/v1/?um=constructor%3A759b6fceb84b20d842bb3ebef1ee8694f7c066ee7fa7a5e87d9d719aada7e9b6&amp;source=constructor" width="100%" height="400" frameborder="0"></iframe>
        </div>
      </div>
    </div>
  </div>
</template>
<script lang="ts" setup>
definePageMeta({
  layout: 'dialog'
})
</script>