<script setup>
const props = defineProps(["operations"]);
</script>

<template>
    <div class="row">
        <ul class="list-group" v-for="item in props.operations">
            <li class="list-group-item">
                {{ `${item.firstNumber} ${item.operation} ${item.secondNumber} = ${item.result} - ${item.feitoEm}` }}
            </li>
        </ul>
    </div>
</template>

<style scoped>

    .list-group{
        display: flex; 
        flex-direction: column; 
        align-items: center;

    }
    .list-group-item{
        width: 600px;
        text-align: center;
        font-size: 24px;
        color: var(--forest);
        margin-bottom: 16px;
    }
</style>