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
    return {};
  },
  computed: {
    sumTotal() {
      if (this.expenseAmountArray.length === 0) {
        const neededItems = JSON.parse(localStorage.getItem("expenses"));
        neededItems.map((data) => {
          this.expenseAmountArray.push(parseInt(data.expense_amount));
        });
        const persistedSumTotal = this.expenseAmountArray.reduce(
          (a, b) => a + b,
          0
        );
        const netAmount = this.annualIncomeAmount - persistedSumTotal;
        return netAmount;
      } else {
        const sumTotal = this.expenseAmountArray.reduce((a, b) => a + b, 0);
        const netAmount = this.annualIncomeAmount - sumTotal;
        return netAmount.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
      }
    },
  },
};
</script>

<style></style>
