<template>
  <div>
    <q-card class="fixed-center q-gutter-md q-pa-md text-body1">
      <div class="q-gutter-md q-pa-md">
        <h4>Validate account</h4>
        <q-btn
          flat
          @click="$router.push({ name: 'validateResend' })"
        >Resend validation code?</q-btn>
        <q-input
          v-model="code"
          label="Code"
          outlined
        />
        <q-btn
          class="q-pa-md"
          label="Validate"
          color="primary"
        />
      </div>
    </q-card>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Validate',
  data: () => ({
    code: ''
  }),
  method: {
    sendValidationCode () {
      axios('http://api-staging.altcoinomy.com/api/v1/validate', {
        method: 'get',
        data: {
          'code': this.code
        }
      }).then(res => {
        console.log(res.data)
      })
    }
  }
}
</script>
<style lang="sass" scoped>
.q-card
  width: 70%
</style>
