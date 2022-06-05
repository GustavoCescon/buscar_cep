<template>
    <div class="row mt-5">
        <div class="col-sm-12 offset-lg-2 col-md-12 col-lg-8 ">      
            <div class="card shadow">
            <div class="card-body">
                <div class="row ">
                    <div class="col-sm-12 col-md-12 col-lg-12 mb-2">
                        <label class="text-secondary fs-6 m-0">Logradouro</label> <br>
                        <span class="fw-bolder">{{logradouro}}</span>                        
                    </div>
                    <div class="col-sm-12 col-md-12 col-lg-12 mb-2">
                        <label class="text-secondary fs-6">Bairro</label> <br>
                        <span class="fw-bolder">{{bairro}}</span>
                    </div>
                    <div class="col-sm-12 col-md-12 col-lg-12 mb-2">
                        <label class="text-secondary fs-6">Localidade/UF</label> <br>
                        <span class="fw-bolder">{{localidade}}-{{uf}}</span>
                    </div>
                    <div class="col-sm-12 col-md-12 col-lg-12 mb-2">
                        <label class="text-secondary fs-6">CEP</label> <br>
                        <span class="fw-bolder">{{meuCep}}</span>
                    </div>
                </div>
            </div>
            </div>      
        </div>
      </div>
</template>

<script >

export default {
    name: "Formulario",
    props:{
        logradouro: String,
        bairro: String,
        localidade: String,
        uf: String,
        meuCep: String,
        visivel: Boolean
    }
}
</script>

<style scoped>
    .card{
        border-top: 5px solid #dc3545;
    }
</style>