<template>
  <div class="modal">
    <div class="modal-content">
      <h2>⏰ Tempo acabou!</h2>
      <p>{{ isFocus ? "Descansa aí agora, mané! 😴" : "Bora trabalhar, preguiçoso! 💪" }}</p>
      <button @click="$emit('close')">Fechar</button>
    </div>
  </div>
</template>

<script lang="ts" setup>
defineProps<{ isFocus: boolean }>();
defineEmits(["close"]);
</script>

<style lang="scss" scoped>
.modal {
  position: fixed;
  inset: 0;
  background: rgba(255, 0, 0, 0.9);
  display: flex;
  justify-content: center;
  align-items: center;

  .modal-content {
    background: #fff;
    padding: 2rem;
    border-radius: 12px;
    text-align: center;

    h2 {
      color: red;
      margin-bottom: 1rem;
      font-size: 2rem;
    }

    p {
      margin-bottom: 1.5rem;
      font-size: 1.2rem;
      color: #222;
      font-weight: bold;
    }

    button {
      background: red;
      color: #fff;
      padding: 0.6rem 1.2rem;
      border-radius: 6px;
      border: none;
      cursor: pointer;
      font-weight: bold;
      &:hover {
        filter: brightness(0.8);
      }
    }
  }
}
</style>
