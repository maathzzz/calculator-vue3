<script setup>
defineProps({
    resultado: String,
});
const emits = defineEmits(['update:resultado']);

</script>

<template>
  <div class="flex h-12 mb-4">
    <div class="flex-auto">
      <input
        type="text"
        required
        placeholder="Digite aqui..."
        :value="resultado"
        @input="$emit('update:resultado', $event.target.value)"
        autocomplete="off"
        class="display"
      />
    </div>
  </div>
</template>

<style scoped>
.display {
    width: 98%;
    height: 70px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    justify-content: center;
    padding: 5px;
    font-size: 30px;
    color: #fff;
    background-color: black;
    border-radius: 10px;
  }</style>