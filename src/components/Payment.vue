<template>
  <div ref="root">
    <h1>Pals</h1>
    <div id="paypal-button-container"></div>
  </div>
</template>

<script>
// import { ref, onMounted } from 'vue'

export default {
  setup() {
    window.paypal.Buttons({
      style: {
        color:'gold',
        shape:'pill'
      },
      createOrder: function(data, actions) {
        // Set up the transaction
        return actions.order.create({
          purchase_units: [{
            amount: {
              value: '0.01'
            }
          }]
        });
      }
    }).render('#paypal-button-container')

    console.log(window.paypal)
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
