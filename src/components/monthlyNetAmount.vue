<template>
  <v-container>
    <h3>Monthly Net Amount</h3>
    <br />
    <h3>${{ sumTotal }}</h3>
  </v-container>
</template>

<script>
export default {
  props: ["expenseAmountArray", "annualIncomeAmount"],
  data() {
    return {
    };
  },
  computed: {
    sumTotal() {
      const sumTotal = this.expenseAmountArray.reduce((a, b) => a + b, 0);
      const netAmount = this.annualIncomeAmount - sumTotal
      return netAmount;
    },
  },
};
</script>

<style></style>
