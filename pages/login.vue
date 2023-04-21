<template>
     <section class="py-[50px] flex flex-col items-center justify-center px-4">
        <div class="text-[32px] font-semibold text-dark mt-[20px] mb-[20px]">
            Sign In
        </div>
        <form class="w-full card shadow-xl" style="width: 30%;" @submit.prevent="userLogin">
            <div class="form-group">
                <label for="" class="text-grey">Email Address</label>
                <input type="email" class="input-field" v-model="login.email">
            </div>
            <div class="form-group">
                <label for="" class="text-grey">Password</label>
                <input type="password" class="input-field" v-model="login.password">
            </div>
            <button type="submit" class="w-full btn btn-primary mt-[14px]">
                Sign In
            </button>
        </form>
    </section>
</template>
<script>
export default {
  data() {
    return {
      login: {
        email: '',
        password: ''
      }
    }
  },
  methods: {
    async userLogin() {
      try {
        let response = await this.$auth.loginWith('local', { data: this.login })
        console.log(response)
      } catch (err) {
        console.log(err)
      }
    }
  }
}
</script>
