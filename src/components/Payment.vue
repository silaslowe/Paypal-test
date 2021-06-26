<template>
  <div ref="root">
    <h1>Pals</h1>
    <div id="paypal-button-container"></div>
  </div>
</template>

<script>
// import { ref, onMounted } from 'vue'

// import {onMounted} from "vue";


export default {
  setup() {
    window.paypal.Buttons({
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

    // onMounted(() => {
    //   let recaptchaScript = document.createElement('script')
    //   recaptchaScript.setAttribute('src', 'https://www.paypal.com/sdk/js?client-id=AYk9nOjy_151hQwR4HDqpytyOzZPOrff1SmXR4qGCC_CcHWH_ElCTOAL6-tVbl-mIM9twh-UPaKCGErU&components=buttons')
    //   document.head.appendChild(recaptchaScript)
    //
    //   console.log(recaptchaScript)
    // })


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
