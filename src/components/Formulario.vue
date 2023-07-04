<script setup>
const props = defineProps(["operation", "trocarFiltro", "registrarOperation", "addNumberOne", "addNumberTwo", "zeroStyle",
    "conditionResult", "conditionDefault"])
</script>
<template>
    <form @submit.prevent="">
        <div class="row">
            <select @change="props.trocarFiltro" class="col-2 m-auto ">
                <option value="" selected>--Operações--</option>
                <option value="somar">Somar</option>
                <option value="subtrair">Subtrair</option>
                <option value="multiplicar">Multiplicar</option>
                <option value="dividir">Dividir</option>
                <option value="resto">Resto</option>
                <option value="raiz">Raiz</option>
                <option value="potencia">Potência</option>
            </select>
        </div>
        <div class="row mt-5">
            <div class="col-6">
                <input type="number" class="form-control" placeholder="Number One" @keyup="props.addNumberOne">
            </div>
            <div class="col-6">
                <input :class="{ zero: props.zeroStyle }" type="number" class="form-control" placeholder="Number Two"
                    @keyup="props.addNumberTwo">
            </div>
        </div>
        <div class="row text-info text-center h1">
            <span v-if="props.conditionResult">
                {{ props.operation }}
                <button @click="props.registrarOperation" class="btn btn-outline-dark">
                    Registre
                </button>
            </span>
            <span v-else-if="props.conditionDefault">
                Preencha os campos
                acima para obter um
                resultado
            </span>
        </div>
    </form>
</template>

<style scoped>
.zero {
    background-color: #0a0202;
    color: #e85555;
    transition: all 0.5s ease;
}
</style>