<template>
  <div>
  <div  class="container">
      <input
        class="inputPesquisa"
        placeholder="Encontre a sua pizza"
        type="search"
        @input="pesquisa = $event.target.value"
      />
  </div>
   <div v-for="pizza in pizzasFiltrados" v-bind:key="pizza.Nome" >
        <div class="Item-pizza">
                <img class="imagemPizza" :src=pizza.Url_imagem >
                <div class="colum">
                    <div class="pizzaNome">{{pizza.Nome}}</div>
                    <div class="pizzaIngredientes">{{pizza.Ingredientes}}</div>
                    <div class="pizzaPreco">{{pizza.Preco}}</div>
                </div>
        </div>
  </div>
  </div>
    
</template>


<script>


export default {
  name: 'Pizzas',
  

  data() {
    return {
      pizzas: [],
      pesquisa: '',
      
    };
  },

  methods: {
    async getPizzas() {
      try {
        const response = await fetch(
          'https://x8ki-letl-twmt.n7.xano.io/api:xR9a0v67/pizzas'
          
        );
        let responseJson = await response.json();
        this.pizzas = responseJson;
      } catch (error) {
        console.log(error);
      }
    },
  },
  

  computed: {
    pizzasFiltrados() {
    
      return this.pizzas.filter(pizza => pizza.Nome.toUpperCase().includes(this.pesquisa.toUpperCase()));
  
    },
  },

  created() {
    this.getPizzas();
  },
};
</script>

<style scoped>

.container {
  
  justify-content: center;
}

.inputPesquisa {
  width: 100%;
  margin-top: 10px;
  margin-bottom: 10px;
  height: 30px;
  border-radius: 5px;
  padding: 5px;
  
  
}
input:focus { 
    outline: none !important;
    border-color: #329845;
  
}
.Item-pizza {
  display: flex;
  width: 100%;

  border: 2px solid gray;
  margin-bottom: 5px;
   border-radius: 5px;
}

.colum {
  flex-direction: column;
  margin-right: 10px;
  flex: 1;
}
.imagemPizza {
  Width: 20%;
  Margin: 10px;

}
.pizzaNome{
color: #329845;
text-align: left;
font-Weight: bold;
margin-top:5px;


}
.pizzaIngredientes {
 color: gray;
 text-align: left;
 font-style: italic;
 
 margin-top:5px;
 

 
}
.pizzaPreco {
  margin-top:5px;
text-align: right;
 color: black;
 font-weight: bold;
}




</style>
