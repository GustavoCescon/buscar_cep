<template>
    <div>
        <div class="alert alert-danger" role="alert">
                {{msg}}
        </div>
    </div>
</template>

<script>
export default{
    name: 'Mensagem',
    props:{
        msg: String
    }
}
</script>
