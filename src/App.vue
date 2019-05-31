<template>
  <div class="bg-primary text-white text-center m-2 p-3">
    <h3>Product: {{ name | reverse | capitalize }}</h3>
    <h3>Price: {{ getTotalPrice(lowTaxRate) | currency(3) }} (Low Rate)</h3>
    <h3>Price: {{ getTotalPrice(highTaxRate) | currency }} (Hight Rate)</h3>
  </div>
</template>

<script>

export default {
  name: 'MyComponent',
  data: function() {
    return {
      name: "Kayak",
      price: 275,
      lowTaxRate: 12,
      highTaxRate: 20
    }
  },
  computed: {

  },
  methods: {
    getTotalPrice(taxRate) {
      return this.price + this.price*taxRate/100;
    }
  },
  filters: {
    currency(value, places) {
      return new Intl.NumberFormat("ua-UA", { 
          style: "currency", 
          currency: "GBP",
          minimumFractionDigits: places || 2,
          maximumFractionDigits: places || 2 
        }).format(value);
    },
    reverse(val) {
      return val.split("").reverse().join("");
    },
    capitalize(val) {
      return val[0].toUpperCase()+val.slice(1);
    }
  }
}
</script>
