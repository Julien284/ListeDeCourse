<template>
  
    <div class="bg-gradient-to-t from-slate-500 to-slate-800  mx-14 my-8 rounded-xl p-10 ">
      
      <p class="flex justify-center  text-white text-xl">Ajouter les produits que vous voulez ajouter a la liste :</p>

      <!-- input -->
      <div class="flex justify-center items-center my-7 ">

        <input type="text" v-model="inputValue" @keyup.enter="validateInput" placeholder="  Entrer un produit"
        class="w-2/4 h-9 rounded-xl bg-slate-300 hover:bg-slate-100 my-4">
        
      </div>



      <!-- Création des divs ajouts -->
      <div id="myDiv" class="grid  gap-x-8 gap-y-4 grid-cols-2 " >

        <div class="flex" v-for="(inputValue, index) in validInputs" :key="index" >
          <div  class="flex justify-center w-full h-9 rounded-l-xl bg-slate-300 hover:bg-slate-100 "  >
            <p class="font-bold">{{ inputValue }}</p> 
          </div>
          
            <button class="bg-slate-600 h-9 w-1/12  rounded-r-xl" @click="removeDiv(index)"> <i class="fa-solid fa-trash"></i></button>
            
        </div>
      </div>
      
    </div>
    
</template>


<script>
export default {
  data() {
    return {
      inputValue: '',
      validInputs: JSON.parse(localStorage.getItem('validInputs')) || [],
      
    }
  },
  methods: {
    validateInput() {
      if (this.inputValue.trim() !== '') {
        this.validInputs.push(this.inputValue);
        localStorage.setItem('validInputs', JSON.stringify(this.validInputs));
        this.inputValue = '';
      }
    },
    removeDiv(index) {
      this.validInputs.splice(index, 1);
      localStorage.setItem('validInputs', JSON.stringify(this.validInputs));
    },
   
  }
}
</script>


