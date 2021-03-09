<template>
  <v-container>
    <h3>Income Section</h3>
    <v-form>
      <v-text-field outlined prepend-inner-icon="$" v-model="annualIncome" @change="updateIncome"/>
    </v-form>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      annualIncome: "",
    };
  },
  mounted(){
    const persistedIncome = localStorage.getItem("annualIncome")
    this.annualIncome = persistedIncome
  },
  methods: {
    updateIncome() {
      const persistedIncome = this.annualIncome
      localStorage.setItem("annualIncome", persistedIncome)
    }
  },
};
</script>

<style></style>
