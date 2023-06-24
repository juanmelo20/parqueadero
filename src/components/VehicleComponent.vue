<script setup>
const props = defineProps({
    tipoVehiculo: {
        type: String,
        default: '-'
     },

})
</script>

<template>
<h1>Vehiculos parqueados</h1>
{{ props }}
</template>