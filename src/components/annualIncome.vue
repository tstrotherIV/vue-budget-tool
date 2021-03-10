<template>
  <v-container>
    <h3>Income Section</h3>
    <v-form>
      <v-text-field
        outlined
        prepend-inner-icon="$"
        v-model="annualIncomeInput"
        @change="updateIncome"
      />
    </v-form>
  </v-container>
</template>

<script>
export default {
  props: ["annualIncomeAmount"],
  data() {
    return {
      annualIncomeInput: 0,
    };
  },
  mounted() {
    this.annualIncomeInput = localStorage.getItem("annualIncomeAmount").toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",")
  },
  methods: {
    updateIncome() {
      this.$emit("income-status-change", this.annualIncomeInput)
    },
  },
};
</script>

<style></style>
