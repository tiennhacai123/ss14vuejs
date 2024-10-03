<template>
  <v-container class="checkout-page">
    <v-card>
      <v-card-title>Item Cart</v-card-title>
      <v-data-table :headers="headers" :items="cartItems" item-value="name">
        <template v-slot:body="{ items }">
          <tbody>
            <tr v-for="item in items" :key="item.name">
              <td>{{ item.name }}</td>
              <td>${{ item.price }}</td>
              <td>
                <v-text-field v-model="item.quantity" type="number" style="width: 80px"></v-text-field>
              </td>
              <td>${{ item.price * item.quantity }}</td>
            </tr>
          </tbody>
        </template>
      </v-data-table>

      <v-card-subtitle class="order-summary">
        <div>
          <p>Sub Total: ${{ subTotal }}</p>
          <p>Discount (5%): -${{ discount }}</p>
          <p>Total: ${{ total }}</p>
        </div>
      </v-card-subtitle>

      <v-btn color="primary" @click="checkout">CheckOut</v-btn>
    </v-card>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      cartItems: [
        { name: 'Cute Soft Teddy Bear', price: 200, quantity: 1 },
      ],
      headers: [
        { text: 'Product', value: 'name' },
        { text: 'Price', value: 'price' },
        { text: 'Quantity', value: 'quantity' },
        { text: 'Total', value: 'total' },
      ],
    };
  },

  methods: {
    checkout() {
      console.log('Proceeding to checkout');
    },
  },
};
</script>

<style scoped>
.checkout-page {
  margin-top: 20px;
}
.order-summary {
  margin-top: 20px;
  text-align: right;
}
</style>
