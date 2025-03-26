<script setup>
import { defineProps } from 'vue'
const props=defineProps({
    usuario:Object
})
</script>
<template>
    <div v-if="usuario" class="hijo">
        <h2>Datos del usuario</h2>
        <p class="texto">Nombre {{usuario.black_nib}}</p>
        <p class="texto">Tu correo es {{usuario["e-mail"] }}</p>
        <p class="texto">Tu edad es de {{ usuario.Calcularedad ? usuario.Calcularedad():"no ingresada"}}</p>
    </div>
    <div v-else>
        <p class="hijo">No hay datos ingresados</p>
    </div>
</template>

<style>
.hijo{
    margin: 10px auto;
    border: 10px solid chocolate;
    background: linear-gradient(rgb(243, 131, 215),rgb(180, 31, 56));
}
</style>