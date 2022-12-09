<template>
  <div class="container column">
    <app-input @block-add="addBlock"></app-input>
    <app-c-v :blockInfo="blockInfo"></app-c-v>
   </div>
  
   <app-comments></app-comments>
  
</template>

<script>
import AppComments from "./AppComments.vue"
import AppInput from "./AppInput"
import AppCV from "./AppCV.vue"

export default {
  data() {
    return {
      blockInfo:[],
    };
  },

  methods: {
    
    addBlock(block) {
      this.blockInfo.push(block)
      
      console.log(this.blockInfo)
      }

  },

  components: { AppComments, AppInput, AppCV},
};
</script>

<style>
.avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>
