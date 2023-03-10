<template>
  <div class="movement">
    <div class="content">
      <h4>{{ title }}</h4>
      <p>{{ description }}</p>
    </div>
    <div class="action">
      <Icon
        @click="deleteMovement(id)"
        icon="mdi:trash-can"
        color="#0689b0"
        width="30"
        height="30"
      />
      <p :class="amountEntero > 0 ? 'green' : 'red'">{{ amountCurrency }}</p>
    </div>
  </div>
</template>

<script setup>
import { Icon } from "@iconify/vue";
import { computed, reactive, toRefs } from "vue";
const props = defineProps(["amount", "description", "title", "id"]);
const { amount, description, title, id } = toRefs(props);
const amountEntero = computed(() => parseInt(amount.value));
console.log(amountEntero);
const emit = defineEmits(["remove"]);
const deleteMovement = () => {
  emit("remove", id.value);
};
const amountCurrency = computed(() =>
  amountEntero.value.toLocaleString("es-CO", {
    style: "currency",
    currency: "COP",
    maximumFractionDigits: 0,
  })
);
</script>

<style scoped>
.movement {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 16px;
  background-color: #e6f9ff;
  border-radius: 8px;
  box-sizing: border-box;
}
.movement .content {
  width: 100%;
}
.movement .action {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  flex-direction: column;
}
h4,
p {
  margin: 0;
  padding: 0;
}
h4 {
  margin-bottom: 8px;
}

.red {
  color: red;
}
.green {
  color: green;
}
</style>