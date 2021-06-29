<template>
  <main>
    <div class="container-fluid c-section">
      <div class="row">
        <div class="col-sm-3"></div>
        <div class="col-sm-6">
          <div class="a-spacing-top-medium"></div>
          <h2>Profile Page</h2>
          <v-btn @click="onLogout">Logout</v-btn>
          <form action="#">
            <!--            Name-->
            <div class="a-spacing-top-medium">
              <!--              Type input-->
              <label for="name">Name</label>
              <input type="text" id="name" style="width: 100%" class="a-input-text" v-model="name"
                     :placeholder="$auth.$state.user.name">
            </div>
            <!--            Email-->
            <div class="a-spacing-top-medium">
              <!--              Type input-->
              <label for="email">Email</label>
              <input type="text" id="email" style="width: 100%" class="a-input-text" v-model="email"
                     :placeholder="$auth.$state.user.email">
            </div>
            <!--            Password-->
            <div class="a-spacing-top-medium">
              <!--              Type input-->
              <label for="password">Password</label>
              <input type="text" id="password" style="width: 100%" class="a-input-text" v-model="password">
            </div>
            <hr>
            <!--            Button-->
            <div class="a-spacing-top-large">
              <span class="a-button-register">
                <span class="a-button-inner">
                  <span class="a-button-text" @click="onUpdateProfile">Update Profile</span>
                </span>
              </span>
            </div>
            <div class="a-spacing-top-large"></div>
          </form>
          <div class="a-spacing-top-large"></div>
        </div>
        <div class="col-sm-3"></div>
      </div>

    </div>
  </main>
</template>

<script>
  export default {
    name: "profile",
    data() {
      return {
        name: "",
        email: "",
        password: ""
      }
    },
    methods: {
      async onUpdateProfile() {
        try {
          let data = {
            name: this.name,
            email: this.email,
            password: this.password
          }
          let response = await this.$axios.$put("/api/auth/user", data);
          if (response.success) {
            this.name = "";
            this.email = "";
            this.password = "";

            await this.$auth.fetchUser();
          }
        } catch (err) {
          console.log(err);
        }
      },
      async onLogout() {
        await this.$auth.logout();
        this.$router.push("/");
        this.$swal("Başarıyla Çıkış Yapıldı");
      }
    }
  }
</script>

<style scoped>

</style>
