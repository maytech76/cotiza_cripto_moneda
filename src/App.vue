<script setup>
  import{ref, onMounted} from 'vue'

    const monedas = ref([
        { codigo: 'USD', texto: 'Dolar de Estados Unidos'},
        { codigo: 'EUR', texto: 'Euro'},
        { codigo: 'CLP', texto: 'Peso Chileno'},
        { codigo: 'MXN', texto: 'Peso Mexicano'},
        { codigo: 'GBP', texto: 'Libra Esterlina'},
    ])

    const criptomonedas = ref([])

   onMounted(()=>{
    const url = 'https://min-api.cryptocompare.com/data/top/mktcapfull?limit=20&tsym=USD'
    fetch(url)
    .then(respuesta =>respuesta.json())
    .then(({Data}) =>criptomonedas.value = Data)
   })


</script>

<template>
 
 <div class="contenedor">
  <h1 class="titulo">Cotizador Online de <span>Criptomonedas</span></h1>

  <div class="contenido">

    <div class="formulario">
      <div class="campo">
        <label for="moneda">Moneda</label>
         <select id="moneda">
            <option value="">-- Selecione una Moneda --</option>
            <option v-for="moneda in monedas" :value="moneda.codigo">{{ moneda.texto }}</option>
         </select>
      </div>
    </div>

  </div>

 </div>
 
</template>


