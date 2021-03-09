<template>
  <v-container>
    <v-row no-gutters>
      <v-col cols="4" class="rounded pa-2">
        <v-card class="pa-2 boxItem">
          <annual-income />
        </v-card>
      </v-col>
      <v-col cols="4" class="rounded pa-2">
        <v-card class="pa-2 boxItem">
          <monthly-net-amount />
        </v-card>
      </v-col>
      <v-col cols="4" class="rounded pa-2">
        <v-card class="pa-2 boxItem">
          <annual-net-amount />
        </v-card>
      </v-col>
    </v-row>
    <v-row no-gutters>
      <v-col cols="6" class="rounded px-2">
        <v-card class="pa-2 boxItem">
          <monthly-expenses
            :expensesList="expensesList"
            @expense-submit="addExpense"
          />
        </v-card>
      </v-col>
      <v-col cols="6" class="rounded px-2">
        <v-card class="pa-2 boxItem">
          <monthly-expense-breakdown />
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import annualIncome from "./annualIncome";
import annualNetAmount from "./annualNetAmount";
import monthlyExpenseBreakdown from "./monthlyExpenseBreakdown";
import monthlyExpenses from "./monthlyExpenses";
import monthlyNetAmount from "./monthlyNetAmount";

export default {
  components: {
    annualIncome,
    annualNetAmount,
    monthlyExpenseBreakdown,
    monthlyNetAmount,
    monthlyExpenses,
  },
  data() {
    return {
      expensesList: [],
    };
  },
  methods: {
    addExpense(formItem) {
      this.expensesList.push(formItem);
    },
  },
};
</script>

<style>
.boxItem {
  height: 100%;
}
</style>
