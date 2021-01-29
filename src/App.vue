<template>
  <div id="app">   
    <h1 class="mt-3 mb-4" style="font-weight: 800;">Empreendimentos</h1>     
    <br>
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-12">
          <div class="row justify-content-center">
            <card v-for="(produto, index) of produtosValidos " :key="produto.name" :produto="produto" :index="index"/>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Produto from './services/produtos'
import card from './components/Card'

export default {
  name: 'App',
  components: {
    card
  },
  data(){
    return {
      produtos: []
    }
  },
  mounted(){
    Produto.listar().then(resposta => {
      this.produtos = resposta.data.products
    })
  },
  methods: {

  },
  computed: {
    produtosValidos: function() {
      return this.produtos.filter(function(u) {
        if(u.address.geo_location && u.address.geo_location.latitude != null && u.address.geo_location.longitude != null && validarArea(u.units.usable_areas)==1){          
          return u
        }
      })
    }       
  }
}

function validarArea(arrayNumeros) {
  var elementoMenor = false;
  if(typeof arrayNumeros == "object"){

    arrayNumeros.forEach(element => {
      if(element < 11){ 
        elementoMenor = true;
      }   
    });
    
    if (elementoMenor){
      return 0
    }
    return 1;              
  }   
  else if(arrayNumeros <= 10){
    return 0;
  } 
  else {
    return 1;
  }
}
</script>

<style>
  #app>h1 {
    text-align: center;
    font-size: 2.5rem;
  }

  * {
    font-family: 'Montserrat', sans-serif;
  }
  
  @media (max-width: 450px){
    #app>h1{
      font-size: 1.6rem;
    }
  }
</style>
