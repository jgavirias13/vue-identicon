<template>
  <div>
    <h3>My Identicon Generator</h3>

    <div>
      Input:
      <input v-on:input="onInput"/>
    </div>

    <div>
      Output:
      <div v-html="identicon" />
    </div>
  </div>
</template>

<script>

import {toSvg} from 'jdenticon';

export default {
  name: 'HelloWorld',
  data() {
    return {
      textInput: ''
    }
  },
  mounted() {
    let recaptchaScript = document.createElement('script')
    recaptchaScript.setAttribute('src', 'https://cdn.jsdelivr.net/gh/dmester/jdenticon@5bbdf8cb/dist/jdenticon.min.js')
    document.head.appendChild(recaptchaScript)
  },
  methods: {
    onInput: function(event) {
      this.textInput = event.target.value;
    }
  },
  computed: {
    identicon: function() {
      return toSvg(this.textInput, 200);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>

//https://cdn.jsdelivr.net/gh/dmester/jdenticon@5bbdf8cb/dist/jdenticon.min.js