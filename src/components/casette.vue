<script setup>
    import { ref, onMounted } from 'vue'
    import cancion1 from './../assets/01. New Jeans.flac'
    import cancion2 from './../assets/01. Supernatural.flac'
    import cancion3 from './../assets/101. OMG.flac'
    import cancion4 from './../assets/09 Ladyfingers.mp3'

// Playlist (usa rutas reales a tus archivos descargados)
const playlist = [
  cancion1,
  cancion2,
  cancion3,
  cancion4
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
                <button id="play" class="estiloBotonesCasette" @click="playSong">⏯</button>
                <button id="pause" class="estiloBotonesCasette" @click="pauseSong">⏸</button>
                <button id="record" class="estiloBotonesCasette" @click="stopSong">⏺</button>
                <button id="next" class="estiloBotonesCasette" @click="nextSong">⏭</button>
                <button id="rewind" class="estiloBotonesCasette" @click="rewindSong">⏪︎</button>
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
    width: 270px;
    height: 150px;
    border-radius: 10px;
    justify-content: center;
}

#medidorDecibelios {
    display: flex;
}

.estiloBotonesCasette {
    border-radius: 10px 10px 10px 10px;
    border: none;
    width: 45px;
    height: 40px;
    margin-top: 5px;
    box-shadow: 3px 3px 5px;
    cursor: pointer;
}

#play {
    background-color: rgb(160, 160, 0);
}

#pause {
    background-color: rgb(107, 0, 0);
}

#record {
    background-color: rgb(0, 0, 105);
}

#next {
    background-color: rgb(141, 92, 0);
}

#rewind {
    border-radius: 10px 10px 10px 10px;
    border: none;
    background-color: rgb(0, 100, 0);
    width: 45px;
    height: 40px;
    margin-top: 5px;
    box-shadow: 3px 3px 5px;
    cursor: pointer;
}

.botonCasette1, .botonCasette2 {
    height: 25px;
    width: 25px;
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
    width: 120px;
    height: 35px;
    padding: 0px 5px 0px 5px;
}

.cuadradoCasette4 {
    background-color: rgb(64, 32, 0);
    border-radius: 5px;
    border: 1px solid white;
    height: 100px;
    width: 250px;
    margin: 10px 0px 0px 10px;
    place-items: center;
    place-content: center;
}

.contenedorLineaCasette {
    display: flex;
    gap: 5px;
    justify-content: center;
}

.lineaCasette {
    background-color: grey;
    border-radius: 20px;
    height: 10px;
    width: 80px;
    margin-top: 15px;
}

.contenedorBotones {
    margin-top: 5%;
    display: flex;
    gap: 10px;
    justify-content: center;
}

</style>