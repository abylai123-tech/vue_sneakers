<script setup>
defineProps({
  totalPrice: Number
})

const emit = defineEmits(['openDrawer']);
</script>

<template>
   <header class="flex justify-between border-b border-slate-300 px-8 py-8">
      <router-link to="/">
        <div class="flex items-center gap-4">
          <img src="/logo.png" alt="Logo" class="w-10 mr-5"/>
          <div>
            <h2 class="text-xl font-bold uppercase">Vue Sneakers</h2>
            <p class="text-slate-500">Магазин лучших  кроссовок</p>
          </div>
        </div>
      </router-link>

      <ul class="flex items-center gap-10">
        <li @click="() => emit('openDrawer')" class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-black">
          <img src="/cart.svg" alt="Cart"/>
          <b>{{ totalPrice }} руб.</b>
        </li>

        <router-link to="/favorites">
          <li class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-black">
            <img src="/heart.svg" alt="Favorites"/>
            <span>Закладки</span>
          </li>
        </router-link>          
        
        <router-link to="/profile">
          <li class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-black">
            <img src="/profile.svg" alt="Cart"/>
            <span>Профиль</span>
          </li>
        </router-link>
      </ul>
    </header>
</template>