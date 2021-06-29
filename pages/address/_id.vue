<template>
  <!--MAIN-->
  <main>
    <!--EDIT ADDRESS-->
    <div class="registerAddress mt-3">
      <div class="container-fluid c-section">
        <div class="row">
          <div class="col-sm-3"></div>
          <div class="col-sm-6">
            <div class="a-section a-spacing-medium">
              <div class="a-subheader a-breadcrumb a-spacing-small">
                <ul>
                  <li>
                    <a href="#">
                      <span>Your Account</span>
                    </a>
                  </li>
                  <li class="a-breadcrumb-divider">›</li>
                  <li>
                    <a href="#">
                      <span>Your Adresses</span>
                    </a>
                  </li>
                  <li class="a-breadcrumb-divider">›</li>
                  <li class="active">
                    <a href="#">
                      <span>Edit Address</span>
                    </a>
                  </li>
                </ul>
              </div>
            </div>
            <div class="a-section">
              <h2>Edit address</h2>
              <div class="a-section a-spacing-none a-spacing-top-small">
                <b>
                  Or pick up your packages at your convenience from our self-service locations. To add an Amazon Pickup
                  Point or Locker, click
                  <a
                    href="#"
                  >here</a>.
                </b>
              </div>
              <!-- Error Message -->
              <div class="a-section a-spacing-none a-spacing-top-small">
                <b></b>
              </div>
              <form>
                <div class="a-spacing-medium a-spacing-top-medium">
                  <!-- Country / Region -->
                  <div class="a-spacing-top-medium">
                    <label for="country" style="margin-bottom: 0px;">Country/Region </label>
                    <select id="country" class="a-select-option" v-model="country">
                      <option value="" selected disabled hidden>{{address.country}}</option>
                      <option v-for="country in countries" :key="country.alpha2Code" :value="country.name">
                        {{country.name}}
                      </option>
                    </select>
                  </div>
                  <!-- Full name -->
                  <div class="a-spacing-top-medium">
                    <label for="fullName" style="margin-bottom: 0px;">Full Name </label>
                    <input :placeholder="address.fullName" id="fullName" type="text" class="a-input-text" style="width: 100%;" v-model="fullName"/>
                  </div>
                  <!-- Street Address -->
                  <div class="a-spacing-top-medium">
                    <label for="streetAddress1" style="margin-bottom: 0px;">Street Address 1</label>
                    <input
                      id="streetAddress1"
                      type="text"
                      class="a-input-text"
                      style="width: 100%;"
                      :placeholder="address.streetAddress"
                      v-model="streetAddress1"
                    />
                    <!-- Street Address 2 -->
                    <label for="streetAddress2" style="margin-bottom: 0px;">Street Address 1</label>
                    <input
                      id="streetAddress2"
                      type="text"
                      class="a-input-text a-spacing-top-small"
                      style="width: 100%;"
                      :placeholder="address.streetAddress"
                      v-model="streetAddress2"
                    />
                  </div>
                  <!-- City -->
                  <div class="a-spacing-top-medium">
                    <label for="city" style="margin-bottom: 0px;">City </label>
                    <input :placeholder="address.city" id="city" type="text" class="a-input-text" style="width: 100%;" v-model="city"/>
                  </div>
                  <!-- State -->
                  <div class="a-spacing-top-medium">
                    <label for="state" style="margin-bottom: 0px;">State / Province / Region </label>
                    <input :placeholder="address.state" id="state" type="text" class="a-input-text" style="width: 100%;" v-model="state"/>
                  </div>
                  <!-- Zip Code -->
                  <div class="a-spacing-top-medium">
                    <label for="zipCode" style="margin-bottom: 0px;">Zip Code </label>
                    <input :placeholder="address.zipCode" id="zipCode" type="text" class="a-input-text" style="width: 100%;" v-model="zipCode"/>
                  </div>
                  <!-- Phone Number -->
                  <div class="a-spacing-top-medium">
                    <label for="phoneNumber" style="margin-bottom: 0px;">Phone Number </label>
                    <input :placeholder="address.phoneNumber" id="phoneNumber" type="text" class="a-input-text" style="width: 100%;"
                           v-model="phoneNumber"/>
                    <div class="a-section a-spacing-none a-spacing-top-micro">
                      <span class="a-size-mini">May be used to assist delivery</span>
                    </div>
                  </div>
                  <div class="a-spacing-base a-spacing-top-medium">
                    <h3>Add delivery instructions</h3>
                  </div>
                  <!-- Delivery Instruction -->
                  <div class="a-spacing-top-medium">
                    <label
                      for="deliverInstructions"
                      style="margin-bottom: 0px;"
                    >Do we need additional instructions to find this address? </label>
                    <textarea
                      id="deliverInstructions"
                      :placeholder="address.deliverInstructions"
                      style="height:6em; width: 100%;"
                      v-model="deliverInstructions"
                    ></textarea>
                  </div>
                  <!-- Security code -->
                  <div class="a-spacing-top-medium">
                    <label
                      for="securityCode"
                      style="margin-bottom: 0px;"
                    >Do we need a security code or a call box number to access this building? </label>
                    <input id="securityCode" type="text" class="a-input-text" style="width: 100%;" :placeholder="address.securityCode"
                           v-model="securityCode"/>
                  </div>
                  <div class="a-spacing-top-medium">
                    <label style="margin-bottom: 0px;">Weekend delivery</label>
                    <a href="#">
                      <i class="fas fa-angle-down"></i> Which days can you receive packages?
                    </a>
                  </div>
                  <div class="a-spacing-top-medium"></div>
                  <hr/>
                  <div class="a-spacing-top-medium">
                    <span>
                      <b>Make sure your address is correct</b>
                    </span>
                  </div>
                  <div>
                    <span>If the address contains typos or other errors, your package may be undeliverable.</span>
                  </div>
                  <div class="a-spacing-top-small">
                    <span>
                      <a href="#">Tips for entering addresses</a>
                    </span>
                    <span>|</span>
                    <span>
                      <a href="#">APO/FPO address tips</a>
                    </span>
                  </div>
                  <div class="a-spacing-top-large">
                    <span class="a-button-register">
                      <span class="a-button-inner">
                        <span class="a-button-text" @click="onUpdateAddress(address._id)">Edit address</span>
                      </span>
                    </span>
                  </div>
                </div>
              </form>
            </div>
          </div>
          <div class="col-sm-3">{{address}}</div>
        </div>
      </div>
    </div>
    <!--/REGISTER ADDRESS-->
  </main>
  <!--/MAIN-->
</template>

<script>
  export default {
    async asyncData({$axios, params}) {
      try {
        let responseCountries = $axios.$get("/api/countries");
        let responseAddress = $axios.$get(`/api/address/${params.id}`);

        const [resCountries, resAddress] = await Promise.all([
          responseCountries,
          responseAddress
        ]);
        return {
          countries: resCountries,
          address: resAddress.address
        };
      } catch (err) {
        console.log(err);
      }
    },
    data() {
      return {
        country: "",
        fullName: "",
        city: "",
        streetAddress1: "",
        streetAddress2: "",
        state: "",
        zipCode: "",
        phoneNumber: "",
        deliverInstructions: "",
        securityCode: "",
      }
    },
    methods: {
      async onUpdateAddress(id) {
        try {
          let data = {
            country: this.country,
            fullName: this.fullName,
            streetAddress: this.streetAddress1 + " / " + this.streetAddress2,
            city: this.city,
            zipCode: this.zipCode,
            phoneNumber: this.phoneNumber,
            deliverInstructions: this.deliverInstructions,
            securityCode: this.securityCode,
          }
          let responseAddresses = await this.$axios.$put(`/api/addresses/${id}`, data);
          if (responseAddresses.success) {
            this.$router.push("/address")
          }
        } catch (err) {
          console.log(err);
        }
      }
    }
  }
</script>

<style scoped>

</style>
