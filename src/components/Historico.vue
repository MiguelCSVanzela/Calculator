<script setup>
const props = defineProps(["operations"]);
</script>

<template>
    <div class="row">
        <ul class="list-group" v-for="item in props.operations">
            <li class="list-group-item">
                {{ `${item.firstNumber} ${item.operation} ${item.secondNumber} = ${item.result}` }}
            </li>
        </ul>
    </div>
</template>