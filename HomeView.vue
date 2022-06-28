<template>
  <div>
    <formulate method="post" @submit.prevent="postNow">
      <div class="form-row">
        <h3>Personal Information</h3>

        <hr />

        <div class="row">
          <div
            class="col-4"
          >Lorem ipsum dolor sit, amet consectetur adipisicing elit. Maxime voluptate, fugit iste molestias soluta sit aliquid consequuntur provident corporis ab aut quam, aliquam harum ullam illum similique qui in suscipit?</div>

          <div class="col-8 text-bold decoration">
            <div class="form-group col-md-6">
              <label >Email</label>
              <FormulateInput type="email"  v-model="form.email"
              autocomplete = "off"
                validation="required|email" />
            </div>
            <div class="form-group col-md-6">
              <label >Password</label>
              <FormulateInput
                type="password"
                
                
                v-model="form.password"
                validation="required|confirm"
              />
            </div>

            <div class="form-group col-md-6">
              <label for="inputAddress">Confirm password</label>
              <input
                type="password"
               
                placeholder="confirm Password"
                v-model="form.confirmation"
                validation="required|Is confermed"
              />
            </div>
            <div class="form-group col-md-6">
             
              <button class="btn btn-primary btn-sm mt-2" @click="postNow">Submit</button>
            </div>
          </div>
        </div>
      </div>
    </formulate>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import axios from "axios";

export default {
  name: "HomeView",
  components: {
    HelloWorld
  },

  data() {
    return {
      form: {
        name: "",
        email: "",
        password: "",
        confirmation: ""
      }
    };
  },
  methods: {
    postNow() {

       
      var formData = new FormData();
      formData.append("email", this.form.email);
      formData.append("password", this.form.password);
      formData.append("confirmation", this.form.confirmation);

      const axioObj = {
        method: "post",
        url: "/v1/users",
        data: formData,
        headers: {
          "Content-type": "multipart/form-data",
          Authorization: "Bearer eb4a35d1-ca5d-487a-b16e-05598fe7a3bb"
        }
      };
      axios(axioObj);

     

     
    }
  }
};
</script>

<style>
.decoration {
  text-decoration: none;
}
</style>
