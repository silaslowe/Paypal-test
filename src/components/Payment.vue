<template>
  <div ref="root">
    <form>
<!--    <InputAmount v-model="input"/>-->
      <input type="text"
             v-model="amount"/>

    <!--      <button type="submit">Submit</button>-->
    </form>
    <div
        id="paypal-button-container"></div>
  </div>
</template>

<script>
import {ref, watch} from 'vue'
// import InputAmount from "./InputAmount";

export default {
  components: {
    // InputAmount
  },
  setup() {
    window.paypal.Buttons({
      style: {
        color: 'gold',
        shape: 'pill'
      },
      createOrder: function (data, actions) {
        // Set up the transaction
        return actions.order.create({
          purchase_units: [{
            amount: {
              value: amount.value
            }
          }]
        });
      },
      onApprove: function (data, actions) {
        return actions.order.capture().then(function (details) {
          // Show a success message to the buyer
          alert('Transaction completed by ' + details.payer.name.given_name + '!');
        });
      }
    }).render('#paypal-button-container')

    const amount = ref("")
    // function onSubmit() {
    //   // submit to backend or whatever you like
    //   console.log(amount);
    // }

    watch(amount, (amount) =>
        console.log(amount))

    console.log(amount)
    return {
      amount
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
