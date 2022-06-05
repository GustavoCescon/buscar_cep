<template>
<div class="container">
  <div class="row">
    <div class="col-sm-12 offset-lg-2 col-md-12 col-lg-8">
      <div class="row">
        <div class="col-sm-12 col-md-12 col-lg-12 text-center p-5 my-5">
          <h1>SEU BUSCADOR DE CEP</h1>          
        </div>
        <div class="col-sm-12 offset-md-2 offset-lg-3 col-md-8 col-lg-6">
          <form class="input-group">
            <input class="form-control" v-model="cep" type="text" placeholder="Digite o CEP" maxlength="8">
            <button type="button" class="btn btn-danger" @click="buscarCep(cep)">Buscar</button>
          </form>
        </div>
        <div class="col-sm-12 offset-md-3 offset-lg-3 col-md-6 col-lg-6 mt-3">
          <Mensagem :msg="msg" v-show="msg"/>
        </div>
      </div>
      <Formulario :logradouro="logradouro" :bairro="bairro" :localidade="localidade" :uf="uf" :meuCep="meuCep" v-show="visivel"/>
    </div>
  </div>
</div>

</template>

<script>
import Mensagem from "./Mensagem.vue"
import Formulario from "./Formulario.vue"

export default {
  name: 'Forms',
  components:{
    Mensagem,
    Formulario
  }, 
  data(){
    return{
      cep: "",
      msg: null,
      logradouro: null,
      bairro: null,
      localidade: null,
      uf: null,
      visivel: false,
      meuCep: null
    }
  },
  methods:{
    async buscarCep(cep){
      if(this.cep.length < 8){
        this.msg = "Este CEP não é valido";
        this.visivel = false;
      }else{
        const req = await fetch(`https://viacep.com.br/ws/${this.cep}/json/`,{
          method: "GET",
          headers: {"Content-Type": "application/json"},
        });
        const data = await req.json();
        if(req.status === 200 && data.erro != "true"){
          this.logradouro = data.logradouro;
          this.bairro = data.bairro;
          this.localidade = data.localidade;
          this.meuCep = data.cep,
          this.uf = data.uf;
          this.visivel = true;
          this.cep="";
          this.msg = "";
        }

        if(data.erro == "true"){
          this.msg = "CEP não encontrado ou não existe";
          this.visivel = false;
          this.cep="";
        }
      }
    }
  }
}
</script>

<style scoped>

</style>
