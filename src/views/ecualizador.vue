<script setup>
import line1 from "./../components/line1.vue"
import line2 from "./../components/line2.vue"
import line3 from "./../components/line3.vue"
import line4 from "./../components/line4.vue"
import line5 from "./../components/line5.vue"
import line6 from "./../components/line6.vue"
import line7 from "./../components/line7.vue"
import line8 from "./../components/line8.vue"
import line9 from "./../components/line9.vue"
import line10 from "./../components/line10.vue"
</script>

<template>
    <div id="table">
        <line1 />
        <line2 />
        <line3 />
        <line4 />
        <line5 />
        <line6 />
        <line7 />
        <line8 />
        <line9 />
        <line10 />
    </div>
</template>

<style scoped>
#table {
    width: 380px;
    display: grid;
    grid-template-columns: repeat(10, 2fr);
    background-color: rgb(209, 209, 209);
    gap: 2px;
}
</style>