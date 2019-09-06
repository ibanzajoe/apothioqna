<template>
  <div class="terms-check">
    <input :value="answer" @input="handleAgreement" type="checkbox" name="agreement" class="check-box" value="true" /> <p>I Agree</p>
  </div>
</template>

<script>
  export default {
    name: "termsCheck",
    data () {
      return {
        checkValue: false
      }
    },
    methods: {
      handleAgreement
    }
  }
</script>

<style scoped>

  .terms-check {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .terms-check input {
    width: 24px;
    height: 24px;
  }
  .terms-check p {
    padding: 1rem;
    line-height: 1rem;
    font-size: 18px;
  }
</style>
