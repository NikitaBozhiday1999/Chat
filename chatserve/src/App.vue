<template>
  <div id="app">
    <ul>
      <history
      v-for = "(item, index) in message" 
      :key  = "item.id"
      @edit-text = "addText(index)">
        {{item.login}} {{item.text}} 
      </history>
    </ul>
    <form @submit.prevent = "addText">
      <input-com v-model.trim="login"></input-com>
      <text-area v-model.trim="text"></text-area>
      <button-sub @click="addText"></button-sub>
    </form>
  </div>
</template>

<script>
import inputComponent from './components/Inputname.vue'
import buttonComponent from './components/Button.vue'
import textareaComponent from './components/Textarea.vue'
import historyComponent from './components/Historychat.vue'

export default {
  components: {
      inputCom: inputComponent,
      buttonSub: buttonComponent,
      textArea: textareaComponent,
      history: historyComponent,
    },
    data() {
      return {
        text: '',
        login: '',
        message: [],
      }
    },
    created() {
      this.addText();
    },
    methods: {
      addText() {
        if (!this.text.length) return;
        console.log(this.message);
          this.message.push({
              text      : this.text,
              login     : this.login,
              id        : this.message.length + 1,
          });
          this.text = '';
          this.login = '';
          console.log(this.message);
      },
      // sendInfo() {

      // }
    }
}
</script>

<style lang="scss">

</style>

