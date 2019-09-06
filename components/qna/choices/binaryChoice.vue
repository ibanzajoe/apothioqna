<template>
  <div class="binary-choice">
    <div class="binary-choices-container flex items-center justify-center">
      <div class="choice-circle flex items-center justify-center"
           v-for="(choice, index) in choices"
           :key="index"
           @click="$emit('selectChoice', choice)"
      >
        {{choice}}
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "binaryChoice",
    props: {
      choices: {
        type: Array,
        default: () => []
      }
    },
    methods: {

    }
  }
</script>

<style scoped>

  .choice-circle {
    width: 122px;
    height: 122px;
    border-radius: 100px;
    border-color: #fff;
    border-width: 4px;
    margin: 10px;

    background-color: #fff;

    font-size: 18px;
    font-weight: 600;
    text-transform: capitalize;
  }
</style>
