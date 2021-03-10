<template>
  <v-container>
    <div>
      <h3>Monthly Expenses</h3>
    </div>
    <div>
      <v-simple-table>
        <template v-slot:default>
          <thead>
            <tr>
              <th class="text-left" id="name">
                Name
              </th>
              <th class="text-left" id="amount">
                Amount
              </th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="expense in expensesList" :key="expense.name">
              <td>{{ expense.expense_name }}</td>
              <td>{{ expense.expense_amount }}</td>
            </tr>
          </tbody>
        </template>
      </v-simple-table>
    </div>
    <hr />
    <div class="">
      <v-row>
        <v-col>
          <h4 class="ma-4">Add expense</h4>
        </v-col>
      </v-row>

      <!-- expenses form -->
      <v-form @submit.prevent="updateExpenses">
        <v-row class="mx-4">
          <v-col>
            <v-text-field
              outlined
              label="Expense Name"
              v-model="form.expense_name"
            />
          </v-col>
          <v-col>
            <v-text-field
              type="number"
              outlined
              label="Expense Amount"
              v-model="form.expense_amount"
            />
          </v-col>
          <v-col>
            <v-btn class="ma-2" fab dark color="indigo" type="submit">
              <v-icon dark>
                mdi-plus
              </v-icon>
            </v-btn>
          </v-col>
        </v-row>
      </v-form>
    </div>
  </v-container>
</template>

<script>
export default {
  props: ["expensesList"],
  data() {
    return {
      form: {
        expense_name: "",
        expense_amount: 0,
      },
    };
  },
  methods: {
    updateExpenses() {
      this.$emit("expense-submit", this.form);
      this.form = {
        expense_name: "",
        expense_amount: 0,
      };
    },
  },
};
</script>

<style></style>
