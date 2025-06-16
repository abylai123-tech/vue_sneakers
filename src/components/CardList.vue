<script setup>
import Card from "./Card.vue";

const onClickAdd = () => {
    alert('Добавить');
}
</script>

<template>
    <div class="grid grid-cols-4 gap-5">
       <Card 
        title="Мужские Кроссовки Nike Blazer Mid Suede" 
        imageUrl="/sneakers/sneakers-1.jpg" 
        :price="5000"
        :isFavorite="false"
        :onClickAdd="onClickAdd"
        :isAdded="true"
       />
       <Card imageUrl="/sneakers/sneakers-2.jpg"/>
       <Card imageUrl="/sneakers/sneakers-3.jpg"/>
       <Card imageUrl="/sneakers/sneakers-4.jpg"/>
       <Card imageUrl="/sneakers/sneakers-5.jpg"/>
       <Card imageUrl="/sneakers/sneakers-6.jpg"/>
       <Card imageUrl="/sneakers/sneakers-7.jpg"/>
       <Card imageUrl="/sneakers/sneakers-8.jpg"/>
       <Card imageUrl="/sneakers/sneakers-9.jpg"/>
       <Card imageUrl="/sneakers/sneakers-10.jpg"/>
       <Card imageUrl="/sneakers/sneakers-11.jpg"/>
       <Card imageUrl="/sneakers/sneakers-12.jpg"/>
    </div>
</template>