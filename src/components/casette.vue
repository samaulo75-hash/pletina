<script setup>
    import { ref, onMounted } from 'vue'
    import cancion1 from './../assets/01. New Jeans.flac'
    import cancion2 from './../assets/01. Supernatural.flac'
    import cancion3 from './../assets/101. OMG.flac'

// Playlist (usa rutas reales a tus archivos descargados)
const playlist = [
  cancion3,
  cancion2,
  cancion1
]

const currentSongIndex = ref(0)
const audio = ref(null)
const isPlaying = ref(false)

onMounted(() => {
  audio.value = new Audio(playlist[currentSongIndex.value])
})

// ▶️ Play
const playSong = () => {
  if (!audio.value) return
  audio.value.play()
  isPlaying.value = true
}

// ⏸️ Pause
const pauseSong = () => {
  if (!audio.value) return
  audio.value.pause()
  isPlaying.value = false
}

// ⏺️ Record (stop total)
const stopSong = () => {
  if (!audio.value) return
  audio.value.pause()
  audio.value.currentTime = 0
  isPlaying.value = false
}

// ⏪ Rewind (reinicia y reproduce)
const rewindSong = () => {
  if (!audio.value) return
  audio.value.currentTime = 0
  audio.value.play()
  isPlaying.value = true
}

// ⏭️ Siguiente canción
const nextSong = () => {
  if (!audio.value) return

  // Parar canción actual
  audio.value.pause()
  audio.value.currentTime = 0

  // Avanzar índice (vuelve a 0 si es la última)
  currentSongIndex.value =
    (currentSongIndex.value + 1) % playlist.length

  // Cargar nueva canción
  audio.value = new Audio(playlist[currentSongIndex.value])

  // Reproducir
  audio.value.play()
  isPlaying.value = true
}

</script>

<template>
    <div id="tabla">
        <div id="contenedorCasette">
            <div id="casette">
                <div class="cuadradoCasette4">
                    <div class="cuadradoCasette3">
                        <div class="botonCasette1"></div>
                        <div class="cuadradoCasette1">
                            <div class="cuadradoCasette2"></div>
                        </div>
                        <div class="botonCasette2"></div>
                    </div>
                </div>
                <div class="contenedorLineaCasette">
                    <div class="lineaCasette"></div>
                    <div class="lineaCasette"></div>
                    <div class="lineaCasette"></div>
                </div>
            </div>
            <div class="contenedorBotones">
                <button id="play" @click="playSong">⏯</button>
                <button id="pause" @click="pauseSong">⏸</button>
                <button id="record" @click="stopSong">⏺</button>
                <button id="next" @click="nextSong">⏭</button>
                <button id="rewind" @click="rewindSong">⏪︎</button>
            </div>
        </div>

        <div id="medidorDecibelios">
            <div>
                <p>db 100</p>
                <p>db 90</p>
                <p>db 80</p>
                <p>db 70</p>
                <p>db 60</p>
                <p>db 50</p>
                <p>db 40</p>
                <p>db 30</p>
                <p>db 20</p>
                <p>db 10</p>
            </div>
            <div class="contenedorBarraMedir">
                <div class="barraMedir"></div>
            </div>
        </div>
    </div>
</template>

<style scoped>

.contenedorBarraMedir {
    margin: 10px;
}

.barraMedir {
    background-color: black;
    width: 30px;
    height: 345px;
    border-radius: 25px;
}

#tabla {
    display: grid;
    grid-template-columns: repeat(2, 2fr);
    place-items: center;
}

#contenedorCasette {
    display: flex;
    flex-direction: column;
}

#casette {
    background-color: black;
    width: 180px;
    height: 100px;
    border-radius: 10px;
    justify-content: center;
}

#medidorDecibelios {
    display: flex;
}

#play {
    border-radius: 10px 10px 10px 10px;
    border: none;
    background-color: rgb(160, 160, 0);
    width: 35px;
    height: 30px;
    margin-top: 5px;
    box-shadow: 3px 3px 5px;
}

#pause {
    border-radius: 10px 10px 10px 10px;
    border: none;
    background-color: rgb(107, 0, 0);
    width: 35px;
    height: 30px;
    margin-top: 5px;
    box-shadow: 3px 3px 5px;
}

#record {
    border-radius: 10px 10px 10px 10px;
    border: none;
    background-color: rgb(0, 0, 105);
    width: 35px;
    height: 30px;
    margin-top: 5px;
    box-shadow: 3px 3px 5px;
}

#next {
    border-radius: 10px 10px 10px 10px;
    border: none;
    background-color: rgb(141, 92, 0);
    width: 35px;
    height: 30px;
    margin-top: 5px;
    box-shadow: 3px 3px 5px;
}

#rewind {
    border-radius: 10px 10px 10px 10px;
    border: none;
    background-color: rgb(0, 100, 0);
    width: 35px;
    height: 30px;
    margin-top: 5px;
    box-shadow: 3px 3px 5px;
}

.botonCasette1, .botonCasette2 {
    height: 17px;
    width: 17px;
    background-color: white;
    border-radius: 50px;
    padding: 5px;
    margin: auto;
    box-shadow: 1px 1px 5px;
}

.cuadradoCasette1 {
    width: 40px;
    height: 12px;
    background-color: wheat;
    border-radius: 2px;
    margin: auto;
    margin-left: 5px;
    margin-right: 5px;
}

.cuadradoCasette3 {
    background-color: grey;
    border-radius: 10px;
    display: flex;
    width: 80px;
    height: 25px;
    padding: 0px 5px 0px 5px;
}

.cuadradoCasette4 {
    background-color: rgb(64, 32, 0);
    border-radius: 5px;
    border: 1px solid white;
    height: 60px;
    width: 160px;
    margin: 10px 0px 0px 10px;
    padding: 15px 0px 0px 40px;
}

.contenedorLineaCasette {
    display: flex;
    gap: 5px;
    margin: 0px 0px 0px 10px;
}

.lineaCasette {
    background-color: grey;
    border-radius: 20px;
    height: 8px;
    width: 50px;
    margin: 10px 0px 0px 0px;
}

.contenedorBotones {
    display: flex;
    gap: 1px;
    justify-content: center;
}

</style>