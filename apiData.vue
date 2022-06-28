<template>
  <div>
    <h1>Hello</h1>

    {{ $route.params.id }}
    <table>
      <tr>
        <td>Id</td>
        <td>{{user.id}}</td>
      </tr>
      <tr>
        <td>Name</td>
        <td>{{user.name}}</td>
      </tr>
      <tr>
      <td>Username</td>
      <td>{{user.username}}</td>
      </tr>
      <tr>
       <td>Address</td>
       <td>{{user.address.city}}</td>
      </tr>
      <tr>
     <td>Email</td>
     <td>{{user.email}}</td>
      </tr>
      <tr>
       <td>street</td>
       <td>{{user.street}}</td>

      </tr>
      <tr>
       <td>Suite</td>
       <td>{{user.suite}}</td>

      </tr>
      <tr>
        <td>city</td>
        <td>{{user.city}}</td>
      </tr>
      <tr>
      <td>zipcode</td>

      </tr>
        <tr>
       <td>website</td>
       <td>{{user.website}}</td>
     
        </tr>
        
        
        
        
        
       
    </table>
  </div>
</template>

<script>
import Vue from "vue";
import VueAxios from "vue-axios";
import axios from "axios";

Vue.use(VueAxios, axios);
export default {
  name: "apiData",

  data() {
    return {
      user: null
    };
  },

  mounted() {
    Vue.axios
      .get(
        "https://jsonplaceholder.typicode.com/users/" + this.$route.params.id
      )
      .then(resp => {
        this.user = resp.data;
      });
  }
};
</script>
