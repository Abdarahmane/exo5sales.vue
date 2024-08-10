<template>
  <div id="app">
    <SaleForm @add-sale="addSale" />
    <SalesTable :sales="sales" />
  </div>
</template>

<script>
import SaleForm from './components/SaleForm.vue'
import SalesTable from './components/SalesTable.vue'

export default {
  components: {
    SaleForm,
    SalesTable
  },
  data() {
    return {
      sales: [],
    };
  },
  methods: {
    addSale(sale) {
      this.sales.push(sale);
    },
  },
};
</script>

