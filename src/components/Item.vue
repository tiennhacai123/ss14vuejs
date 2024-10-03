<template>
  <v-container class="product-details">
    <v-row>
      <v-col cols="6">
        <v-carousel>
          <v-carousel-item v-for="image in product.images" :key="image">
            <v-img :src="image"></v-img>
          </v-carousel-item>
        </v-carousel>
      </v-col>
      <v-col cols="6">
        <v-card>
          <v-card-title>{{ product.title }}</v-card-title>
          <v-card-subtitle v-if="product.discount">
            <span class="discount-price">Before: ${{ product.originalPrice }}</span>
            <span>Now: ${{ product.discountedPrice }}</span>
          </v-card-subtitle>
          <v-card-subtitle v-else>
            ${{ product.price }}
          </v-card-subtitle>
          <v-rating :value="product.rating" readonly></v-rating>
          <v-select label="Colors" :items="product.colors"></v-select>
          <v-text-field label="Quantity" type="number" v-model="quantity"></v-text-field>
          <v-btn color="primary">Buy Now</v-btn>
          <v-btn outlined color="secondary">Add to Cart</v-btn>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      product: {
        title: 'Cute Soft Teddy Bear',
        images: ['https://masta.vn/wp-content/uploads/2023/03/teaser.jpg', 'https://macone.vn/wp-content/uploads/2023/03/Macbook-Pro-2023.png'],
        price: 200,
        discount: true,
        originalPrice: 250,
        discountedPrice: 200,
        rating: 4.5,
        colors: ['Red', 'Blue', 'Green'],
      },
      quantity: 1,
    };
  },
};
</script>

<style scoped>
.product-details {
  margin-top: 20px;
}
.discount-price {
  text-decoration: line-through;
  color: red;
}
</style>
