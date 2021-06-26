<template>
  <div class="home">
    <Payment />
  </div>
</template>

<script>
// @ is an alias to /src
import Payment from '@/components/Payment.vue'

export default {
  name: 'Home',
  components: {
    Payment
  }
}
</script>
