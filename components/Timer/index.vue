<template>
  <div class="laptop-container">
    <p class="hot-shot">GORĄCY STRZAŁ</p>
    <img src="/timer/lapek.png" alt="Laptop Lenovo" class="laptop-image">
    <p class="opis">Lenovo V17 i5-1335U/16GB/512/Win11P</p>
    <p class="cena">3254,00 zł</p>
      <div class="timer">
      <div class="time-block">
        <div class="time-value">{{ formatTime(hours) }}</div>
        <div class="time-label">godz.</div>
      </div>
      <div class="separator">:</div>
      <div class="time-block">
        <div class="time-value">{{ formatTime(minutes) }}</div>
        <div class="time-label">min</div>
      </div>
      <div class="separator">:</div>
      <div class="time-block">
        <div class="time-value">{{ formatTime(seconds) }}</div>
        <div class="time-label">sek</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      totalSeconds: 7200, // 2 godziny w sekundach
      intervalId: null,
      hours: 0,
      minutes: 0,
      seconds: 0,
    };
  },
  mounted() {
    this.startTimer();
  },
  methods: {
    startTimer() {
      this.intervalId = setInterval(() => {
        if (this.totalSeconds > 0) {
          this.hours = Math.floor(this.totalSeconds / 3600);
          this.minutes = Math.floor((this.totalSeconds % 3600) / 60);
          this.seconds = this.totalSeconds % 60;
          this.totalSeconds--;
        } else {
          this.stopTimer();
          // Odtwórz dźwięk powiadomienia lub wykonaj inne działania po zakończeniu odliczania
        }
      }, 1000);
    },
    stopTimer() {
      clearInterval(this.intervalId);
    },
    formatTime(value) {
      return value.toString().padStart(2, '0');
    },
  },
};
</script>

<style lang="scss" scoped>
@import './timer.scss';
</style>
