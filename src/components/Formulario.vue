<script setup>
const props = defineProps([ "operation", "trocarFiltro", "registrarOperation", "addNumberOne", "addNumberTwo", "addYear",  "zeroStyle",
    "conditionResult", "conditionDefault", "useResultado"])

</script>
<template>
    <form @submit.prevent="">
        <div class="row">
            <select @change="props.trocarFiltro" class="col-2 m-auto operation-container ">
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
        <div class="row mt-5 input-container">
                <input type="number" class="form-control text-center inputOne" placeholder="Number One" @keyup="props.addNumberOne">
    
                <input :class="{ zero: props.zeroStyle }" type="number" class="form-control text-center inputSecond" placeholder="Number Two"
                    @keyup="props.addNumberTwo">
        </div>
        <div class="row text-center">
            <div  v-if="props.conditionResult" class="result-container">
                <span class="result">
                    {{ props.operation }}
                </span>
                <button @click="props.registrarOperation" class="button">
                    Registre
                </button>
                <button @click="props.useResultado" class="button">
                    Use
                </button>
            </div>
            <div class="form-title" v-else-if="props.conditionDefault">
                Preencha os campos
                acima para obter um
                resultado
            </div>
        </div>
    </form>
</template>

<style scoped>
.zero {
    background-color: var(--dark);
    color: var(--rose);
    transition: all 0.5s ease;
}

.operation-container{
    border-radius: 8px;
    font-size: 24px;
    text-align: center;
}
.input-container{
    display: flex; 
    justify-content: center;
    flex-direction: row;
    margin-bottom: 20px;
}
.form-control{
    width: 400px;
    margin: 0 16px;
    box-shadow: none;
}

.button{
    color: var(--forest);
    border: 0.5px solid var(--forest);
    border-radius: 8px;
    background-color: transparent;
    text-transform: uppercase;
    margin: 16px 10px;
    font-size: 32px;
    transition: all 0.3s ease;
}

.button:hover{
    color: var(--white); 
    background-color: var(--forest);
}

.result-container{
    display: flex;
    justify-content: center;
    align-items: center;
}

.result{
    color: var(--dark); 
    font-size: 24px;
    border: 1px solid var(--dark); 
    padding: 6px;
    margin-right: 8px;
    border-radius: 8px;
}
.form-title {
    color: var(--dark);
    font-size: 32px;
}
</style>