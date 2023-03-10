<template>
  <main>
    <p>{{ labelShowed }}</p>
    <h1>{{ amountShowed }}</h1>
    <div class="graphic">
      <slot name="graphic"></slot>
    </div>
    <div class="action">
      <slot name="action"></slot>
    </div>
  </main>
</template>

<script setup>
import { computed, toRefs } from "vue";

const props = defineProps({
  totalAmount: { type: Number },
  amount: { type: Number, default: null },
  label: String,
});
const { amount, label, totalAmount } = toRefs(props);
const amountShowed = computed(() => {
  const amounted = amount.value ? amount.value : totalAmount.value;
  return amounted.toLocaleString("es-CO", {
    style: "currency",
    currency: "COP",
    maximumFractionDigits: 0,
  });
});
const labelShowed = computed(() => (label.value ? label.value : "Monto total"));
</script>


<style scoped>
main {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
}

h1,
p {
  margin: 0;
  text-align: center;
}

h1 {
  margin-top: 14px;
  color: var(--brand-green);
}

.graphic {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  padding: 48px 24px;
  box-sizing: border-box;
}
</style>
