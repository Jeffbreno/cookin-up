<script setup lang="ts">

import Tag from './Tag.vue';
import { ref } from 'vue';

const props = defineProps({ ingrediente: { type: String, required: true } });
const { ingrediente } = props;
const selecionado = ref(false);

const emit = defineEmits(['adicionarIngrediente', 'removerIngrediente']);

const aoClicar = () => {
    selecionado.value = !selecionado.value;
    if (selecionado.value) {
        emit('adicionarIngrediente', ingrediente);
    } else {
        emit('removerIngrediente', ingrediente);
    }
}

</script>

<template>
    <button class="ingrediente" @click="aoClicar" :aria-pressed="selecionado">
        <Tag :texto="ingrediente" :ativa="selecionado" />
    </button>
</template>

<style scoped>
.ingrediente {
    cursor: pointer;
}
</style>