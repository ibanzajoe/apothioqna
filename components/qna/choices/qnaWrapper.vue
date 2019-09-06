<template>
  <div class="qna-wrapper">
    <div class="qna-wrapper-question-container">
      <slot name="question-slot"/>
    </div>
    <div class="qna-wrapper-choices-container">
      <slot name="choices-slot" />
    </div>

  </div>
</template>

<script>
  export default {
    name: "qnaWrapper"
  }
</script>

<style scoped>

  .qna-wrapper-question-container {
    margin-bottom: 30px;
  }

  .qna-wrapper-choices-container {
    padding: 0 2rem;
  }
</style>
