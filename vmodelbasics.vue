<template>
  <div class="row">
    <div class="col-5 ">
      <h3>Register Form</h3>
      <form  >
      <label>Name:-</label>
      <input type="text" v-model = "name" />
      <br /><br />

      <label>Email:-</label>
      <input type="text"  v-model = "email" />
      <br /><br />

      <label>Password :-</label>
      <input type="password"  v-model = "password" />
      <br /><br />
      <b-button variant="success" @click="submit">Submit</b-button>

      </form>
    </div>

    <div class="col-6">
    <table class="table">
     <tr>
        <td>Name</td>
        <td>Email</td>
        <td>Password</td>
     </tr>
     <tr v-for="item in items" :key="item.id">
        <td>{{item.name}}</td>
        <td>{{item.email}}</td>
        <td>{{item.password}}</td>
       
     </tr>
    

    </table>

    </div>
  </div>
</template>

<script>
export default {
  name: "vmodelBasics",
   

   data(){
    return{
        
        name: '',
        email: '',
        password: '',
        items:[]
    }
   },
   methods:{
     submit(){
        console.log('input' +this.name+ " "+ this.email+ ' '+ this.password);
        this.items.push({
            name: this.name,
            email: this.email,
            password : this.password
        });
        this.clearForm();
     },
     clearForm(){
        this.name = "";
        this.email = "" ;
        this.password = ""
     }

   }

};
</script>
