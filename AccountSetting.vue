<template>
  <div>
    <h1>Account Setting Page</h1>
    <div class="row">
      <div class="col-8">
        <table class="table">
          <tr>
            <td>Id</td>
            <td>Name</td>
            <td>Username</td>
            <td>Address</td>
            <td>Email</td>
            <td>Company</td>
          </tr>
          <tr v-for="item in list" v-bind:key="item.id">
            <td>
              <router-link :to=" '/apiData/'+ item.id">{{('#')+item.id}}</router-link>
            </td>
            <td>{{item.name}}</td>
            <td>{{item.username}}</td>
            <td>{{item.address.city}}</td>
            <td>{{item.email}}</td>
            <td>{{item.company.name}}</td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import VueAxios from "vue-axios";
import axios from "axios";

Vue.use(VueAxios, axios);

export default {
  name: "AccountSetting",

  data() {
    return {
      list: undefined
    };
  },

  mounted() {
    Vue.axios.get("https://jsonplaceholder.typicode.com/users").then(resp => {
      this.list = resp.data;
      console.log(resp.data);
    });
  }
};
</script>