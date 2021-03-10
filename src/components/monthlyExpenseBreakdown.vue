<template>
  <v-card height="100%">
    <v-card-title class="purple--text">Monthly Expense Breakdown</v-card-title>
    <apexchart type="pie" :options="options" :series="series" height="300" />
  </v-card>
</template>

<script>
export default {
  props: ["expensesList", "annualIncomeAmount"],
  computed: {
    series() {
      return this.expensesList.map((e) => parseInt(e.expense_amount));
    },
    options() {
      return {
        labels: this.expensesList.map((e) => e.expense_name),
      };
    },
  },
};
</script>

<style></style>
