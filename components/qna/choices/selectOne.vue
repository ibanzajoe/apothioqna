<template>
  <div class="select-one-container flex justify-center flex-wrap">
    <div class="select-one flex justify-start items-center"
         :class="{'has-many': choices.length > 4}"
         v-for="(choice, index) in choices"
         :key="index"
         @click="$emit('selectChoice', choice)"
    >
      <div class="select-one-image flex justify-center items-center">

      </div>
      <div class="select-one-label ml-4">
        {{choice.label}}
      </div>
    </div>

  </div>
</template>

<script>
  export default {
    name: "selectOne",
    props: {
      choices: {
        type: Array,
        default: () => []
      }
    },
    data () {
      return {

      }
    }
  }
</script>

<style scoped>

  .select-one {
    padding: 1rem;
    background-color: #fff;
    border: 4px solid #fff;
    width: 100%;
    margin: 4px 8px;
    border-radius: 100px;
  }
  .select-one.has-many {
    width: auto;
    padding: 0.5rem 1rem;
    padding-right: 3rem;
  }
  .select-one-image {
    width: 30px;
    height: 30px;
    border-radius: 100px;
    border: 3px solid #f4f1ed;
  }
  .select-one-label {
    font-size: 18px;
    font-weight: 600;
    text-transform: capitalize;
  }
</style>
