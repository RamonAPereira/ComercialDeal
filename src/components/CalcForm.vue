<template>
  <form class="calcform" @submit.prevent="calculateBonusCost">
    <div class="calcform_section">
      <label for="totalCost">Custo total</label>
      <input id="totalCost" v-model.number="totalCost" type="number" />
    </div>

    <div class="calcform_section">
      <label for="paidAmount">Quantidade de unidades compradas</label>
      <input id="paidAmount" v-model.number="paidAmount" type="number" />
    </div>

    <div class="calcform_section">
      <label for="bonusAmount">Quantidade de unidades bonificadas</label>
      <input id="bonusAmount" v-model.number="bonusAmount" type="number" />
    </div>

    <button type="submit">Calcular</button>
  </form>

  <div>
    <p>{{ bonusCost }}</p>
  </div>
</template>

<script setup>
import { ref } from "vue";

const totalCost = ref(0);
const paidAmount = ref(0);
const bonusAmount = ref(0);
const bonusCost = ref(0);

const calculateBonusCost = () => {
  bonusCost.value = totalCost.value / (paidAmount.value + bonusAmount.value);
};
</script>
<style scoped>
.calcform {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 2rem;
}
.calcform_section {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 0.5rem;
}
</style>
