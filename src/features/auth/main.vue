<template>   
  <div class="login-wrap">
    <div class="login-html">
      
      <input 
        id="tab-1" 
        type="radio"
        value="signin" 
        name="tab" 
        class="sign-in" 
        @change="navigate"
        v-model="navigation" checked><label for="tab-1" class="tab">Sign In</label>

      <input 
        id="tab-2" 
        type="radio"
        value="signup" 
        name="tab" 
        class="sign-up" 
        @change="navigate"
        v-model="navigation"><label for="tab-2" class="tab">Sign Up</label>

      <div class="login-form">
        <sign-in @do-sign-in="doSignIn"/>
        <sign-up />
      </div>

    </div>
  </div>
</template>

<script>
  import SignIn from './sign-in'
  import SignUp from './sign-up'
  export default {
    components: {
      SignIn,
      SignUp
    },
    data () {
      return {
        navigation: 'signin'
      }
    },
    methods: {
      navigate () {
        this.$bus.$emit('navigate', this.navigation)
      },
      doSignIn (obj) {
        // Fingindo uma chamada ajax
        console.log(obj)
      }
    }
  }
</script>

<style src="./styles.css"></style>
