<template>
  <v-container>
    <h3>Annual Net Amount</h3>
    <br />
    <h3>${{ sumNetAmount }}</h3>
  </v-container>
</template>

<script>
export default {
  props: ["expenseAmountArray"],
  computed: {
    sumNetAmount() {
      const sumTotal = this.expenseAmountArray.reduce((a, b) => a + b, 0);
      const netAmount = sumTotal * 12;
      return netAmount;
    },
  },
};
</script>

<style></style>
