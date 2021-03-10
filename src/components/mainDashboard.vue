<template>
  <v-container>
    <v-row no-gutters>
      <!-- Annual Income Section -->
      <v-col cols="4" class="rounded pa-2">
        <v-card class="pa-2 boxItem">
          <annual-income
            :annualIncomeAmount="annualIncomeAmount"
            @income-status-change="updateIncome"
          />
        </v-card>
      </v-col>

      <!-- Monthly Net Amount -->
      <v-col cols="4" class="rounded pa-2">
        <v-card class="pa-2 boxItem">
          <monthly-net-amount
            :expenseAmountArray="expenseAmountArray"
            :annualIncomeAmount="annualIncomeAmount"
          />
        </v-card>
      </v-col>

      <!-- Annual net Amount -->
      <v-col cols="4" class="rounded pa-2">
        <v-card class="pa-2 boxItem">
          <annual-net-amount :expenseAmountArray="expenseAmountArray" />
        </v-card>
      </v-col>
    </v-row>

    <!-- Monthly Expenses Section -->
    <v-row no-gutters>
      <v-col cols="6" class="rounded px-2">
        <v-card class="pa-2 boxItem">
          <monthly-expenses
            :expensesList="expensesList"
            @expense-submit="addExpense"
            :totalOfExpenses="totalOfExpenses"
          />
        </v-card>
      </v-col>

      <!-- Monthly Expense Graph Section -->
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
      totalOfExpenses: 0,
      annualIncomeAmount: 0,
      expenseAmountArray: [],
    };
  },
  mounted() {
    const persistedExpenses = localStorage.getItem("expenses");
    this.expensesList = JSON.parse(persistedExpenses) || [];

    const persistedTotalExpenses = localStorage.getItem("expensesTotal");
    this.totalOfExpenses = JSON.parse(persistedTotalExpenses) || "";

    const persistedAnnualIncome = localStorage.getItem("annualIncomeAmount");
    this.annualIncomeAmount = persistedAnnualIncome;
  },
  methods: {
    addExpense(formItem) {
      this.expensesList.push(formItem);
      localStorage.setItem("expenses", JSON.stringify(this.expensesList));

      this.expenseAmountArray.push(parseInt(formItem.expense_amount));
    },
    updateIncome(amount) {
      this.annualIncomeAmount = amount;
      localStorage.setItem("annualIncomeAmount", amount)
    },
  },
};
</script>

<style>
.boxItem {
  height: 100%;
}
</style>
