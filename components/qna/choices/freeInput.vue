<template>
  <div class="choice-freeform" :class="{'is-filled': freeForm}">
    <input v-on:keyup.enter="$emit('send', freeForm)" class="choice-input" v-model="freeForm" />
    <button @click="$emit('send', freeForm)" class="next-button" :disabled="!freeForm">

    </button>
  </div>
</template>

<script>
  export default {
    name: "freeInput",
    props: {
      answer: {
        type: String,
        default: null
      }
    },
    mounted() {
      this.freeForm = this.answer
    },
    data () {
      return {
        freeForm: null
      }
    }
  }
</script>

<style rel="stylesheet/scss"  scoped>
  .choice-freeform {
    background: #fff;
    border: 3px solid #3e306e;
    border-radius: 7px;
    display: flex;
    max-width: 570px;
    padding: 1.5rem 0;
    transition: border-color 800ms;
    width: 100%;
    justify-content: center;
    align-items: center;
    margin: 1rem auto;
    line-height: 1.625;
  }
  .choice-input {
    background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAASCAYAAABSO15qAAAAAXNSR0IArs4c6QAAAPhJREFUOBHlU70KgzAQPlMhEvoQTg6OPoOjT+JWOnRqkUKHgqWP4OQbOPokTk6OTkVULNSLVc62oJmbIdzd95NcuGjX2/3YVI/Ts+t0WLE2ut5xsQ0O+90F6UxFjAI8qNcEGONia08e6MNONYwCS7EQAizLmtGUDEzTBNd1fxsYhjEBnHPQNG3KKTYV34F8ec/zwHEciOMYyrIE3/ehKAqIoggo9inGXKmFXwbyBkmSQJqmUNe15IRhCG3byphitm1/eUzDM4qR0TTNjEixGdAnSi3keS5vSk2UDKqqgizLqB4YzvassiKhGtZ/jDMtLOnHz7TE+yf8BaDZXA509yeBAAAAAElFTkSuQmCC");
    background-repeat: no-repeat;
    background-attachment: scroll;
    background-size: 16px 18px;
    background-position: 98% 50%;
    font-size: 26px;
    padding: 0 2rem;
    border-radius: 5px;
    box-shadow: none;
    box-sizing: border-box;
    color: #000;
    transition: border 400ms ease;
    width: 100%;
    display: block;
    outline: 0;
    border-width: 0;
  }
  .next-button {
    font-size: 16px;
    border-radius: 100px;
    border-style: solid;
    display: inline-block;
    line-height: 20px;
    text-decoration: none;
    transition: color 400ms, background-color 400ms, border 400ms, width 400ms cubic-bezier(0.09, 1, 0.205, 1);
    user-select: none;
    vertical-align: middle;
    white-space: nowrap;
    background-color: #f1574b;
    border-color: #f1574b;
    border-width: 3px;
    flex: 0 0 auto;
    height: 28px;
    margin-right: 1rem;
    overflow: hidden;
    padding: 0;
    position: relative;
    width: 28px;
    outline: none;
  }
  .next-button:disabled {
    background-color: #dadada;
    border-color: #dadada;
    color: rgba(0,0,0,0.2);
    cursor: not-allowed;
    pointer-events: none;
    background-image: url(./images/arrow-white.svg);
    background-position: center;
  }
  .next-button:before, .next-button:after {
      transition-duration: 200ms;
  }
  .next-button:hover:before, .next-button:hover:after {
      background-color: #fff;
      background-image: url(./images/next-arrow.svg);
      background-position: center;
  }
  .next-button:before {
    background-image: url(./images/arrow-white.svg);
    opacity: 1;
    padding-left: 0.25rem;
    padding-top: 0.5rem;
    background-position: center;
    bottom: 0;
    content: '';
    height: 100%;
    left: 0;
    position: absolute;
    width: 100%;
  }
  .next-button:after {
    background-image: url(./images/arrow-white.svg);
    bottom: -1rem;
    display: inline-block;
    opacity: 0;
    right: 0;
  }
  .next-button:before, .next-button:after {
    background-position: center;
    content: '';
    height: 100%;
    left: 0;
    position: absolute;
    width: 100%;
  }
  @media screen and (max-width: 444px) {
    .choice-freeform {
      padding: 1rem;
    }
    .choice-input {
      font-size: 16px;
      padding-left: 0.5rem
    }
    .next-button {
      width: 20px;
      height: 20px;
    }
  }
</style>
