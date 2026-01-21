<script setup>
import { ref } from 'vue';

const medidor = ref(0)
const max = 94
const paso = 2
const min = 0

const subir = () => {
    if (medidor.value < max) {
        const medidorSube = medidor.value += paso
        console.log(medidorSube);
    }
} 

const bajar = () => {
    if (medidor.value > min) {
        const medidorBaja = medidor.value -= paso
        console.log(medidorBaja);
        
    }
}
</script>

<template>
   <div class="contenedor">
        <button 
            @click="bajar" 
            class="aumentar"
        >
        </button>
        <div class="barra">
            <div 
                class="medidor"
                :style="{ top: medidor + '%'}"
            >
            </div>
        </div>
        <button 
            @click="subir" 
            class="disminuir"
        >
        </button>
        <p>500</p>
   </div>
</template>

<style scoped>
.contenedor {
    display: flex;
    flex-direction: column;
    align-items: center;
    height: 380px;
}

.barra {
    background-color: black;
    border-radius: 70px;
    position: relative;
    width: 8px;
    height: 380px;
}

.aumentar {
    width: 14px;
    height: 18px;
    background-color: gray;
    border-radius: 100%;
    margin-bottom: 8px;
}

 .disminuir {
    width: 14px;
    height: 18px;
    background-color: rgb(220, 220, 220);
    border-radius: 50%;
    margin-top: 8px;
}

.medidor {
    border-radius: 100px;
    position: absolute;
    top: 60%;
    width: 18px;
    height: 18px;
    background-color: rgb(203, 203, 203);
    margin: 0px 5px 0px -5px;
    box-shadow: 0px 4px 6px;
}
</style>