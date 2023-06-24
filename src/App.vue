<script setup>
import { ref } from 'vue';
import VehicleComponent from './components/VehicleComponent.vue';
const tiempoRegistro = ref(0)
const fecha = new Date
const tiemoInicio= fecha.getTime
console.log('tiempo de entrada '+ tiemoInicio)

function registrar(){
const fechaIngreso = new Date
const day = fechaIngreso.getDate()
const month = fechaIngreso.getMonth()+1
const year = fechaIngreso.getFullYear()
const time = fechaIngreso.getTime()
const final =time/60000
tiempoRegistro.value=final
console.log('tiempo en minutos'+tiempoRegistro.value)
console.log('fecha de ingreso'+ day+'/'+ month+'/'+year)
return day+'/'+ month+'/'+year
}
function salida(){
const fechaSalida = new Date
const timeSalida = fechaSalida.getTime()
const finalt =timeSalida/60000
console.log('salir:'+finalt)
if(finalt >  tiempoRegistro.value){
     const tiempotranscurrido = finalt - tiempoRegistro.value
     console.log('tiempo transcurrido en minutos'+tiempotranscurrido)
     return tiempotranscurrido.value
  }
  
}
let typeVehicle
let placa
const arrayVehiculos=[
  {
    tipoVehiculo:typeVehicle,
    placa:placa,
    fechaHoraIngreso:registrar(),
  }
]
</script>

<template>

  <div>
    <p class="m-auto w-max  bg-blue-600 rounded-sm text-white text-center text-2xl">PARQUEADERO JC</p> <br>
    <div class="mb-4 bg-blue-300 text-center ml-24 mr-24 rounded-lg">
      <h1 class="text-white text-2xl ">Tarifas de parqueo</h1>
      <h2>PESADOS: $2000 por 15 minutos</h2>
      <h2>AUTOMOVIL: $1000 por 15 minutos</h2>
      <h2>MOTOCICLETA: $500 por 15 minutos</h2>
    </div>
      <h1 class="flex justify-center bg-slate-800 border-2 mr-60 ml-60 border-black rounded-md text-white">Tipo de AUTOMOVIL</h1>
      <div class="flex justify-center items-center mt-2">
        <div>
        <span>INGRESA TIPO DE VEHICULO</span>
        <input class="border-4 border-blue-800 rounded-md " placeholder="Tipo de vehiculo" type="text" v-model="typeVehicle" >
        <span>PLACA</span>
        <input type="text" class="border-4 border-blue-800 rounded-md " placeholder="#placa" v-model="placa">
        <button @click="registrar" class="border-2 mt-4 bg-green-500 rounded-md border-green-900">REGISTRAR</button> <br>
        <button @click="salida" class="border-2 mt-4 bg-green-500 rounded-md border-green-900">cobrar</button> <br>
      </div>
      <div><VehicleComponent v-for="(vehicle,index) in arrayVehiculos()" 
        :key="index" :tipoVehiculo="vehicle"/></div>
    </div>
  </div>
</template>

