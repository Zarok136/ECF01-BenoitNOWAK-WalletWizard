<script setup>
import {ref , computed} from 'vue'

let id = 0
const Ndepense = ref()
const Ddepense = ref('')
const Tdepense = ref([])


//Permet d'ajouter une dépense ainsi que sa déscription sous forme d'objet dans le tableau Tdepense
const addDepense = (desc, mtn) =>{
  Tdepense.value.push({id: id++,desc: desc, mtn: mtn})
  Ndepense.value=''
  Ddepense.value=''
}
//Retourne un nouveau tableau avec uniquement les chiffres du tableau 'Tdepense' et additionne 
//le tout pour ressortir un total
const changeT = computed(()=>{
  const map = Tdepense.value.map((x) => x.mtn);
  const sommeT = map.reduce((a,b)=> a+b,0)
  return sommeT
})

</script>

<template>
<div class="sorties">

<h2>Sorties:</h2>

<form @submit.prevent="addDepense(Ddepense,Ndepense)">

<!--Enregistrer une dépense-->

  <label for="dépense">Entrez une nouvelle dépense : </label>
  <input type="number" name="dépense" placeholder="ex: 50" v-model="Ndepense" required>

  <!--Enregistrer la description de la dépense-->
  <label for="desc">Description: </label>
  <input type="text" name="desc" v-model="Ddepense">
  <button>Enregistrer</button>
</form>



<!--ENREGISTREMENT AJOUT DES DEPENSES-->
  <div class="cardDepense">
    <h2>Dépenses enregistrées:</h2>
    <ul v-for="e in Tdepense">
      <li>Descritpion: {{ e.desc }}  Coût: {{ e.mtn }}€</li>
    </ul>
  </div>
<!--TOTAL-->
<div class="total">
    <p>Total de vos dépenses: {{ changeT }} €</p>
  </div>
</div>

</template>

<style scoped>
.sorties{
  display: flex;
  flex-direction: column;
  margin-top: 5rem;
  align-items: center;
}

form{
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
