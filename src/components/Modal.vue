<template>
  <div class="modale">
    <div class="head">
      <p>Nuevo movimiento</p>
      <Icon
        width="30"
        height="30"
        icon="material-symbols:close"
        color="red"
        @click="close"
      />
    </div>
    <div class="body">
      <slot></slot>
    </div>
  </div>
</template>

<script setup>
import { defineEmits } from "vue";
import { Icon } from "@iconify/vue";
const emit = defineEmits(["close"]);
const close = () => emit("close");
</script>

<style scoped>
.modale {
  z-index: 2;
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  background-color: white;
}
.head {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 24px 24px;
  box-sizing: border-box;
}
p {
  margin: 0;
  font-size: 1.5rem;
  color: var(--brand-blue);
}
</style>