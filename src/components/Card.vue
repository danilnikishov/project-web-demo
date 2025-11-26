<script setup>
defineProps({
  id: Number,
  title: String,
  imageUrl: String,
  price: Number,
  isFavorite: Boolean,
  isAdded: Boolean,
  onClickAdd: Function,
  onClickFavorite: Function,
})
</script>

<template>
  <div
    class="relative bg-white border border-slate-100 rounded-3xl p-6 sm:p-8 cursor-pointer transition-all duration-300 hover:-translate-y-2 hover:shadow-xl"
  >
    <!-- Иконка избранного - КРУПНЕЕ -->
    <img
      v-if="onClickFavorite"
      :src="!isFavorite ? '/like-1.svg' : '/like-2.svg'"
      alt="Like 1"
      class="absolute top-4 left-4 w-8 h-8 sm:top-5 sm:left-5 sm:w-9 sm:h-9 md:top-6 md:left-6 md:w-10 md:h-10 lg:top-8 lg:left-8 lg:w-11 lg:h-11 z-10 hover:scale-110 transition-transform"
      @click="onClickFavorite"
    />

    <!-- Изображение товара - КРУПНЕЕ -->
    <img
      :src="imageUrl"
      alt="sneaker"
      class="w-40 h-40 xs:w-44 xs:h-44 sm:w-48 sm:h-48 md:w-52 md:h-52 lg:w-56 lg:h-56 xl:w-60 xl:h-60 mx-auto object-contain mb-5"
    />

    <!-- Название - КРУПНЕЕ -->
    <p
      class="mt-3 text-lg xs:text-xl sm:text-2xl md:text-2xl font-semibold line-clamp-2 text-gray-800 min-h-16 flex items-center"
    >
      {{ title }}
    </p>

    <div class="flex justify-between items-center mt-5 sm:mt-6 md:mt-7">
      <div class="flex flex-col">
        <span class="text-slate-400 text-base sm:text-lg md:text-xl">Цена:</span>
        <b class="text-xl sm:text-2xl md:text-3xl lg:text-4xl text-gray-900">{{ price }} руб.</b>
      </div>

      <!-- Иконка добавления - КРУПНЕЕ -->
      <img
        v-if="onClickAdd"
        @click="onClickAdd"
        :src="!isAdded ? '/plus.svg' : '/checked.svg'"
        alt="Plus"
        class="w-9 h-9 sm:w-10 sm:h-10 md:w-11 md:h-11 lg:w-12 lg:h-12 hover:scale-110 transition-transform cursor-pointer"
      />
    </div>
  </div>
</template>
