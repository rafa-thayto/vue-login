<template>
  <!-- Sign in -->
  <form action="#" @submit.prevent="submit" class="sign-in-htm">
    <div class="group">
      <label 
        :class="{ invalid: $v.username.$dirty && $v.username.$invalid }"
        for="sing-in-user1"
        class="label">Username</label>
      <input 
        :class="{ invalid: $v.username.$dirty && $v.username.$invalid }" 
        id="sing-in-user1"
        type="text"
        @input="$v.username.$touch()"
        class="input" v-model="username">
    </div>
    <div class="group">
      <label 
        :class="{ invalid: $v.password.$dirty && $v.password.$invalid }" 
        for="sing-in-pass1" 
        class="label">Password</label>
      <input 
        :class="{ invalid: $v.password.$dirty && $v.password.$invalid }" 
        id="sing-in-pass1" 
        type="password" 
        data-type="password" 
        @input="$v.password.$touch()"
        class="input" v-model="password">
    </div>
    <div class="group">
      <input id="check" type="checkbox" class="check" v-model="keepSignedIn">
      <label for="check"><span class="icon"></span> Keep me Signed in</label>
    </div>
    <div class="group">
      <input type="submit" class="button" value="Sign In">
    </div>
    <div class="hr"></div>
    <div class="foot-lnk">
      <a href="#forgot">Forgot Password?</a>
    </div>
  </form>
</template>

<script>
import { required } from 'vuelidate/lib/validators'

export default {
  mounted () {
    this.$bus.$on('navigate', selected => this.reset(selected))
  },
  validations: {
    username: {
      required
    },
    password: {
      required
    }
  },
  data () {
    return {
       username: '',
       password: '',
       keepSignedIn: false
    }
  },
  methods: {
    submit () {
      if (!this.$v.$invalid) {
        this.$emit('do-sign-in', {...this.$data})
      } else {
        this.$v.$touch();
      }
    },
    reset (selected) {
      if (selected === 'signup') {
        this.username = ''
        this.password = ''
        this.keepSignedIn = true
        this.$v.$reset()
      }
    }
  },
  computed: {
    isValid () {
      return !this.$v.username.$invalid && !this.$v.password.$invalid
    }
  }
}
</script>
