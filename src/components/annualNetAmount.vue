<template>
  <v-container>
    <h3>Annual Net Amount</h3>
    <br />
    <h3>${{ sumNetAmount }}</h3>
  </v-container>
</template>

<script>
export default {
  props: ["expenseAmountArray", "annualIncomeAmount"],
  computed: {
    sumNetAmount() {
      const sumTotal = this.expenseAmountArray.reduce((a, b) => a + b, 0);
      const netAmount = sumTotal * 12;
      const annualAmont = this.annualIncomeAmount * 12
      return (annualAmont - netAmount).toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
  },
};
</script>

<style></style>
