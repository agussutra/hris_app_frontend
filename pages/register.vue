<template>
    <section class="py-[50px] flex flex-col items-center justify-center px-4">
        <div class="text-[32px] font-semibold text-dark mt-[20px] mb-[20px]">
            Sign Up
        </div>
        <form class="w-full card" style="width: 30%;" @submit.prevent="userRegister">
            <div class="form-group">
                <label for="" class="text-grey">Name</label>
                <input type="text" class="input-field" v-model="register.name">
            </div>
            <div class="form-group">
                <label for="" class="text-grey">Email Address</label>
                <input type="email" class="input-field" v-model="register.email">
            </div>
            <div class="form-group">
                <label for="" class="text-grey">Password</label>
                <input type="password" class="input-field" v-model="register.password">
            </div>
            <button type="submit" class="w-full btn btn-primary mt-[14px]">
                Continue
            </button>
        </form>
    </section>
</template>
<script>
export default {
 auth: 'guest',
  data() {
    return {
      register: {
        name:'',
        email: '',
        password: ''
      }
    }
  },
  methods: {
    async userRegister() {
      try {
        let response = await this.$axios.post('/register', this.register);

        // if successfull, login user
        try {
            let login = await this.$auth.loginWith('local',{
                data: {
                    email: this.register.email,
                    password: this.register.password,
                },
            })
            console.log(login)
        } catch (err) {
            console.log(err)
        }
        console.log(response)
      } catch (error) {
        console.log(error)
      }
    }
  }
}
</script>