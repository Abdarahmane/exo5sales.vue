<template>
    <div class="container mt-4">
      <h2>Enregistrer une vente</h2>
      <form @submit.prevent="submitForm">
        <div class="form-group">
          <label for="reference">Référence</label>
          <input v-model="reference" type="text" id="reference" class="form-control" />
          <span v-if="errors.reference" class="text-danger">{{ errors.reference }}</span>
        </div>
        <div class="form-group">
          <label for="designation">Désignation</label>
          <input v-model="designation" type="text" id="designation" class="form-control" />
          <span v-if="errors.designation" class="text-danger">{{ errors.designation }}</span>
        </div>
        <div class="form-group">
          <label for="quantity">Quantité</label>
          <input v-model="quantity" type="number" id="quantity" class="form-control" />
          <span v-if="errors.quantity" class="text-danger">{{ errors.quantity }}</span>
        </div>
        <div class="form-group">
          <label for="price">Prix de vente</label>
          <input v-model="price" type="number" id="price" class="form-control" step="0.01" />
          <span v-if="errors.price" class="text-danger">{{ errors.price }}</span>
        </div>
        <button type="submit" class="btn btn-primary">Enregistrer</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        reference: '',
        designation: '',
        quantity: '',
        price: '',
        errors: {},
      };
    },
    methods: {
      validateForm() {
        this.errors = {};
        let valid = true;
  
        if (!this.reference) {
          this.errors.reference = 'La référence est requise.';
          valid = false;
        }
        if (!this.designation) {
          this.errors.designation = 'La désignation est requise.';
          valid = false;
        }
        if (!this.quantity || this.quantity <= 0) {
          this.errors.quantity = 'La quantité doit être un nombre positif.';
          valid = false;
        }
        if (!this.price || this.price <= 0) {
          this.errors.price = 'Le prix de vente doit être un nombre positif.';
          valid = false;
        }
  
        return valid;
      },
      submitForm() {
        if (this.validateForm()) {
          this.$emit('add-sale', {
            reference: this.reference,
            designation: this.designation,
            quantity: this.quantity,
            price: this.price,
          });
  
          this.reference = '';
          this.designation = '';
          this.quantity = '';
          this.price = '';
          this.errors = {};
        }
      },
    },
  };
  </script>
  