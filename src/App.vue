<script setup>
import Formulario from './components/Formulario.vue'
import Clima from './components/Clima.vue'
import Spínner from './components/Spínner.vue'
import Alerta from './components/Alerta.vue'
import useClima from './composables/useClima'

const { obtenerClima, clima, mostrarClima, cargando, error } = useClima()
</script>

<template>
	<h1 class="titulo">Buscador de clima</h1>
	<div class="contenedor buscador-clima">
		<Formulario @obtener-clima="obtenerClima" />
		<Spínner v-if="cargando" />
		<Alerta v-if="error">{{ error }}</Alerta>
		<Clima :clima="clima" v-if="mostrarClima" />
	</div>
</template>
