<template>
  <layout>
    <template #header>
      <Header />
    </template>
    <template #resume>
      <Resume :label="date" :amount="amount" :totalAmount="500000">
        <template #graphic> <Graphic /> </template>
        <template #action> <action></action> </template>
      </Resume>
    </template>
    <template #movements>
      <movements :movements="ListaMovimientos" />
    </template>
  </layout>
</template>

<script setup>
import Graphic from "@/components/Resume/Graphic.vue";

import Layout from "./Layout.vue";
import Header from "./Header.vue";
import Resume from "@/components/Resume/index.vue";
import Movements from "./Movements/index.vue";
import Action from "./Action.vue";
import { reactive, ref } from "vue";
const amount = ref(null);
const date = ref(null);
const ListaMovimientos = reactive([
  {
    id: 1,
    title: "Movimiento 5",
    description: "Deposito de salario",
    amount: "1000",
  },
  {
    id: 2,
    title: "Movimiento 1",
    description: "Deposito de honorarios",
    amount: "500",
  },
  {
    id: 3,
    title: "Movimiento 3",
    description: "Comida",
    amount: "-100",
  },
  {
    id: 4,
    title: "Movimiento 4",
    description: "Colegiatura",
    amount: "1000",
  },
  {
    id: 5,
    title: "Movimiento 5",
    description: "Reparación equipo",
    amount: "1000",
  },
]);
</script>

<style lang="scss" scoped>
</style>