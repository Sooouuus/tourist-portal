<script setup lang="ts">
import BurgerMenu from './BurgerMenu.vue';


</script>
<template>
    <div class="header-area">
        <img src="../public/images/logo.svg" class="logo-size">
        <!-- <MenuButton buttonText="Меню"></MenuButton> -->
         <BurgerMenu></BurgerMenu>
    </div>
</template>

<style scoped>
.logo-size{
    width: 29px;
}
.header-area{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}
</style>