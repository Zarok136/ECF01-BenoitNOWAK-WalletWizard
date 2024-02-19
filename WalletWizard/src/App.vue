<script setup>
import AddMoney from './components/AddMoney.vue';
import WalletWizard from './components/WalletWizard.vue';
</script>

<template>
  <nav>
  <h1 class="titre">Wallet Wizard</h1>
  <img src="../public/Wizard.png" alt="">
  </nav>
<div class="content">
<WalletWizard/>
<AddMoney/>
</div>
</template>

<style scoped>


.content{
  margin: 0;
  background-color: #0C1821;
  height: 100dvh;
  width: 100dvw;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-template-rows: 1fr;
  grid-column-gap: 0px;
  grid-row-gap: 0px;
  color: #F2F3F4;
}

.titre{
  color: white;
  background-color: #0C1821;
  margin: auto;
  text-align: center;
  font-size: 3rem;
  font-family: "Lumanosimo", cursive;
}

img{
  position: absolute;
  width: 10rem;
  top:47rem;
  left: 105rem;
}
</style>
