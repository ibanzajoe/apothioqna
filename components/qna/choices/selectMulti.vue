<template>
  <div class="select-multi-container flex justify-center flex-wrap">
    <div class="select-multi-item flex-initial"
         v-for="(choice, index) in choices"
         :key="index"
         @click="$emit('selectChoice', choice)"
    >
      <div class="select-multi-item-image flex justify-center items-center">
        <img :src="choice.icon" alt="image" />
      </div>
      <div class="select-multi-item-label">
        <p>
          {{choice.label}}
        </p>

      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "selectMulti",
    props: {
      choices: {
        type: Array,
        default: () => []
      }
    }
  }
</script>

<style scoped>

  .select-multi-item {
    padding: 0 1rem;
  }

  .select-multi-item-image {
    width: 60px;
    height: 60px;
    margin: 0 auto;

    border-radius: 100px;
    border: 4px solid #ffffff;
    background-color: #ffffff;
  }

  .select-multi-item-label {
    font-size: 14px;
  }

  .select-multi-item-label p {
    margin: 14px auto;
    text-align: center;
    min-height: 42px;
    max-width: 72px;
  }
</style>
