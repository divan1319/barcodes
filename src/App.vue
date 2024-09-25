<script setup>
import VueBarcode from '@chenfengyuan/vue-barcode';
import html2pdf from "html2pdf.js";
import { ref } from 'vue';
const codes = ref([
{"codigo": "wzVTs4bQ"},
  {"codigo": "mv2gdnI3"},
  {"codigo": "hJXiWOLs"},
  {"codigo": "54DmGwWY"},
  {"codigo": "RbpTlDWV"},
  {"codigo": "jId12ciC"},
  {"codigo": "rMw8pz37"},
  {"codigo": "K4HiIMly"},
  {"codigo": "hTXvwnH5"},
  {"codigo": "fyX4dg1a"},
  {"codigo": "ieFSm5Cs"},
  {"codigo": "4vxLEY8U"},
  {"codigo": "Mrab7eN0"},
  {"codigo": "mO20nhYN"},
  {"codigo": "Ve4ZqnWy"},
  {"codigo": "B6AQanRp"},
  {"codigo": "rE0UBwnd"},
  {"codigo": "kCMmawxS"},
  {"codigo": "8lhbH2vW"},
  {"codigo": "iq1bGzr8"},
  {"codigo": "AtixLUOo"},
  {"codigo": "3GiuPeMv"},
  {"codigo": "9suQCM1v"},
  {"codigo": "0IPAnT2q"},
  {"codigo": "zqUSpuD3"},
  {"codigo": "cTNnA9tQ"},
  {"codigo": "kWmLVHsi"},
  {"codigo": "lADf2HS7"},
  {"codigo": "v2sZ0jKu"},
  {"codigo": "mr7bLJIu"}
])

const generate = ()=>{
  html2pdf(document.getElementById("codes_bar"),{
    margi:1,
    filename:'codes.pdf'
  })
}
</script>

<template>
<div id="codes_bar" class="grid grid-cols-5 px-2 py-2 gap-y-24" >
  <vue-barcode v-for="(code,i) in codes" :key="i" :value="code.codigo" tag="img" class="border-red-400 border"></vue-barcode>
</div>
<button class="h-10 w-20 bg-blue-600" @click="generate">Generar</button>
</template>

