<script setup>
import {ref} from 'vue'
let id = 0
const Nentree = ref()
const Dentree = ref('')
const Tentree = ref([])

const addEntree = (desc, mtn) =>{
  Tentree.value.push({id: id++,desc: desc, mtn: mtn})
  Nentree.value=''
  Dentree.value=''
  console.log(Tentree.value);
}
</script>

<template>
  <div class="entrees">
  <h2>Entrées:</h2>
    <!--AJOUT D'ARGENT-->
<div class="AddMoneyCard">
  <form @submit.prevent="addEntree(Dentree,Nentree)">

    <!--ARGENT-->
    <label for="ajout">Entrez une entrée d'argent: </label>
    <input type="number" name="ajout" placeholder="ex: 100" v-model="Nentree" required>

    <!--DESCRIPTION-->
    <label for="desc">Description: </label>
  <input type="text" name="desc" v-model="Dentree">

  <button>Enregistrer</button>

  </form>
</div>

<div class="cardDepense">

<!--ENREGISTREMENT AJOUT D'ARGENT-->
    <h2>Ajout d'argent enregistrées:</h2>
    <ul v-for="e in Tentree">
      <li>Descritpion: {{ e.desc }}  Ajout: {{ e.mtn }}€</li>
    </ul>
  </div>
</div>
</template>

<style scoped>
.entrees{
  
  display: flex;
  flex-direction: column;
  margin-top: 5rem;
  align-items: center;
}

form{
  font-size: 2rem;
  border: 0.1rem solid #F2F3F4;
  padding: 1rem;
  border-radius: 1rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

button{
  margin-top: 1rem;
  font-size: 1.5rem;
  border: 0.1rem solid #F2F3F4;
  color: #F2F3F4;
  background-color: #0C1821;
  border-radius: 0.5em;
  transition: all 400ms ease;
}

button:hover {
  cursor: pointer;
  transform: scale(1.05, 1.1);
  background-color: #F2F3F4;
  color: #0C1821;
        }

.cardDepense{
  margin-top: 2rem;
}
</style>
