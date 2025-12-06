<template>
  <div class="pomodoro">
    <div class="pomodoro-modal">
      <h1>{{ isFocus ? 'Tempo de Foco' : 'Tempo de Descanso' }}</h1>

      <div class="timer-display">
        {{ formattedTime }}
      </div>

      <div class="actions">
        <button @click="startTimer">▶️ Start</button>
        <button @click="pauseTimer">⏸ Pause</button>
        <button @click="resetTimer">🔄 Reset</button>
      </div>

      <TimerModal v-if="showModal" :isFocus="isFocus" @close="closeModal" />
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref, computed, onUnmounted } from 'vue'
import TimerModal from './TimerModal.vue'

const FOCUS_TIME = 25 * 60
const BREAK_TIME = 5 * 60

const isFocus = ref(true)
const timeLeft = ref<number>(FOCUS_TIME)
const showModal = ref(false)
const timer = ref<number | null>(null)

const formattedTime = computed(() => {
  const m = String(Math.floor(timeLeft.value / 60)).padStart(2, '0')
  const s = String(timeLeft.value % 60).padStart(2, '0')
  return `${m}:${s}`
})

function startTimer() {
  if (timer.value) return

  timer.value = window.setInterval(() => {
    if (timeLeft.value > 0) {
      timeLeft.value--
    } else {
      stopTimer()
      showModal.value = true
    }
  }, 1000)
}

function stopTimer() {
  if (timer.value !== null) {
    clearInterval(timer.value)
    timer.value = null
  }
}

function pauseTimer() {
  stopTimer()
}

function resetTimer() {
  stopTimer()
  timeLeft.value = isFocus.value ? FOCUS_TIME : BREAK_TIME
}

function closeModal() {
  showModal.value = false
  isFocus.value = !isFocus.value
  resetTimer()
}

onUnmounted(stopTimer)
</script>

<style lang="scss" scoped>
.pomodoro {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 70vh;
  text-align: center;
  font-family: sans-serif;
  padding: 2rem;

  .pomodoro-modal {
    border: 1px solid #FF0000;
    border-radius: 12px;
    display: flex;
    flex-direction: column;
    align-items: center;
    max-width: 700px;
    padding: 2rem;

    h1 {
      margin-bottom: 1rem;
    }

    .timer-display {
      font-size: 5rem;
      font-weight: bold;
      margin-bottom: 1.5rem;
      text-shadow: 0px 4px 12px rgba(255,0,0);
    }

    .actions {
      display: flex;
      justify-content: center;
      gap: 1rem;

      button {
        background: #222;
        color: #fff;
        border: 1px solid #FF0000;
        padding: 10px 20px;
        border-radius: 8px;
        cursor: pointer;
        font-size: 1rem;
        transition: 0.2s;

        &:hover {
          background-color: #FF000040;
          box-shadow: 1px 1px 15px 5px #FF0000;
        }
      }
    }
  }
}
</style>
