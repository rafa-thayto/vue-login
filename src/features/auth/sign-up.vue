<template>
  <!-- Sign up -->
  <form action="#" @submit.prevent="submit" class="sign-up-htm">
    <div class="group">
      <label 
        :class="{ invalid: $v.username.$dirty && $v.username.$invalid }"
        for="sign-up-user2" 
        class="label">Username</label>
      <input 
        :class="{ invalid: $v.username.$dirty && $v.username.$invalid }"
        @input="$v.username.$touch()"
        id="sign-up-user2" 
        type="text" 
        v-model="username"
        class="input">
    </div>
    <div class="group">
      <label 
        :class="{ invalid: $v.password.$dirty && $v.password.$invalid }"
        for="sign-up-pass1" 
        class="label">Password</label>
      <input 
        :class="{ invalid: $v.password.$dirty && $v.password.$invalid }"
        @input="$v.password.$touch()"
        id="sign-up-pass1" 
        type="password" 
        v-model="password"
        class="input" data-type="password">
    </div>
    <div class="group">
      <label 
        :class="{ invalid: $v.password2.$dirty && $v.password2.$invalid }"
        for="sign-up-pass2" 
        class="label">Repeat Password</label>
      <input 
        :class="{ invalid: $v.password2.$dirty && $v.password2.$invalid }"
        @input="$v.password2.$touch()"
        id="sign-up-pass2" 
        type="password" 
        v-model="password2"
        class="input" data-type="password">
    </div>
    <div class="group">
      <label 
        :class="{ invalid: $v.email.$dirty && $v.email.$invalid }"
        for="pass" 
        class="label">Email Address</label>
      <input 
        :class="{ invalid: $v.email.$dirty && $v.email.$invalid }"
        @input="$v.email.$touch()"
        id="pass" 
        type="text" 
        v-model="email"
        class="input">
    </div>
    <div class="group">
      <input type="submit" class="button" value="Sign Up">
    </div>
    <div class="hr"></div>
    <div class="foot-lnk">
      <label for="tab-1">Already Member?</label>
    </div>
  </form>
</template>

<script>
import { required, sameAs, email } from 'vuelidate/lib/validators'

export default {
  mounted () {
    this.$bus.$on('navigate', this.reset)
  },
  validations: {
    username: {
      required
    },
    password: {
      required
    },
    password2: {
      required,
      sameAsPassword: sameAs('password')
    },
    email: {
      required,
      email
    },
  },
  data () {
    return {
      username: '',
      password: '',
      password2: '',
      email: ''
    }
  },
  methods: {
    submit () {
      if (!this.$v.$invalid) {
        this.$emit('do-sign-up', {...this.$data})
      } else {
        this.$v.$touch()
      }
    },
    reset (selected) {
      if (selected === 'signin') {
        this.username = ''
        this.password = ''
        this.password2 = ''
        this.email = ''
        this.$v.$reset()
      }
    }
  }
}
</script>
