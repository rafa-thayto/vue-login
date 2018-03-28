<template>
  <!-- Sign up -->
  <form action="#" @submit.prevent="submit" class="sign-up-htm">
    <div class="group">
      <label for="sign-up-user2" class="label">Username</label>
      <input id="sign-up-user2" type="text" class="input">
    </div>
    <div class="group">
      <label for="sign-up-pass2" class="label">Password</label>
      <input id="sign-up-pass2" type="password" class="input" data-type="password">
    </div>
    <div class="group">
      <label for="sign-up-confirm-pass2" class="label">Repeat Password</label>
      <input id="sign-up-confirm-pass2" type="password" class="input" data-type="password">
    </div>
    <div class="group">
      <label for="pass" class="label">Email Address</label>
      <input id="pass" type="text" class="input">
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
export default {
  mounted () {
    this.$bus.$on('navigate', obj => {
      console.log({
        onde: 'signup',
        obj
      })
    })
  },
  data () {
    return {

    }
  }
}
</script>
