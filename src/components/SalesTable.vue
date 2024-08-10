<template>
    <div class="container mt-4">
      <h2>Ventes enregistrées</h2>
      <table class="table table-striped">
        <thead>
          <tr>
            <th>Référence</th>
            <th>Désignation</th>
            <th>Quantité</th>
            <th>Prix de vente</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(sale, index) in sales" :key="index">
            <td>{{ sale.reference }}</td>
            <td>{{ sale.designation }}</td>
            <td>{{ sale.quantity }}</td>
            <td>{{ sale.price.toFixed(2) }} €</td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  export default {
    props: ['sales'],
  };
  </script>
  