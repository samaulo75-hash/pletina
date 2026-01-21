<script setup>

</script>

<template>
<div class="db-meter">
    <div class="db-scale">
        <span>100</span>
        <span>80</span>
        <span>60</span>
        <span>40</span>
        <span>20</span>
        <span>0</span>
    </div>
    <div class="db-bar-container">
        <div class="db-bar"></div>
    </div>

    <p class="db-label">dB</p>
</div>
</template>

<style>
.db-meter {
  width: 120px;
  height: 260px;
  background: #dcdcdc;
  border-radius: 8px;
  display: flex;
  align-items: center;
  padding: 10px;
  box-shadow: inset 0 0 6px rgba(0,0,0,0.3);
  font-family: serif;
}

.db-scale {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  margin-right: 8px;
  font-size: 12px;
}

.db-scale span {
  color: #000;
}

.db-bar-container {
  position: relative;
  width: 20px;
  height: 100%;
  background: #aaa;
  border-radius: 10px;
  overflow: hidden;
}

.db-bar {
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 30%;
  background: #000;
  border-radius: 10px;
  animation: dbMove 2s infinite ease-in-out;
}

.db-label {
  writing-mode: vertical-rl;
  transform: rotate(180deg);
  margin-left: 6px;
  font-weight: bold;
}

</style>