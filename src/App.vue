<script setup>
import VueBarcode from '@chenfengyuan/vue-barcode';
import html2pdf from "html2pdf.js";
import { v4 as uuidv4 } from 'uuid';
import { onMounted, ref } from 'vue';

const barcodes = ref([])

const generateCode = ()=>{
  while(barcodes.value.length <170){
    const newCodes = uuidv4().replace(/-/,'').slice(0,10)
    if(!barcodes.value.find(bc=> bc.codigo === newCodes)){
      barcodes.value.push({codigo:newCodes})
    }
  }

}

const generate = ()=>{
  html2pdf(document.getElementById("codes_bar"),{
    margi:1,
    filename:'codes.pdf'
  })
}

onMounted(()=>{
  generateCode()
})
</script>

<template>
<div id="codes_bar" class="grid grid-cols-2 px-2 py-2  gap-x-20 gap-y-24 bg-gray-500 w-full" >
  <vue-barcode v-for="(code,i) in barcodes" :key="i" :value="code.codigo" tag="img" class="border-slate-900 border w-full"></vue-barcode>
</div>
<button class="h-10 w-20 bg-blue-600" @click="generate">Generar</button>
</template>

