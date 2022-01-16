<template>
  <v-row>
    <v-col class="text-center">
      <v-text-field label="email" v-model="email"></v-text-field>
      <v-text-field label="password" v-model="password"></v-text-field>
      <v-btn @click="login" color="blue" outlined>ログイン</v-btn>
    </v-col>
    {{ $auth.loggedIn }}
  </v-row>
</template>

<script>
export default {
  data() {
    return {
      email: "poppotennis@test.com",
      password: "password",
    };
  },
  created() {
    console.log(this.$auth.loggedIn);
  },
  methods: {
    async login() {
      try {
        let response = await this.$auth.loginWith("local", {
          data: {
            email: this.email,
            password: this.password,
          },
        });
        console.log(response);
      } catch (err) {
        console.log(err);
      }
      //   console.log("おした");
      //   this.$axios
      //     .$post("/api/login", {
      //       email: this.email,
      //       password: this.password,
      //     })
      //     .then((response) => {
      //       console.log(response);
      //     });
    },
  },
};
</script>
