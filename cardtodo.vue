<template>
  <div class="row">
    <div class="col-5">
      <h3>Registration Form</h3>
      <form>
        <label>Name:- </label>
        <input type="text" v-model="name" /> <br /><br />

        <label>Email :-</label>
        <input type="text" v-model="email" /> <br /><br />

        <label>Address :- </label>
        <input type="text" v-model="address" /> <br /><br />
        <b-button variant="success" @click="submit">Submit</b-button>
      </form>
    </div>
    <div class="col-6">
      <b-card-group deck>
        <b-card
          bg-variant="success"
          text-variant="white"
          header="Success"
          class="text-center"
        >
          <b-card-text>
            <div class="row">
              <div class="col-4">Name</div>
              <div class="col-4">Email</div>
              <div class="col-4">Address</div>


            </div>

              <div class="row" v-for="item in items" :key="item.id">
                <div class="col-4">{{ item.name }}</div>
                <div class="col-4">{{ item.email }}</div>
                <div class="col-4">{{ item.address }}</div>
              </div>
          </b-card-text>
        </b-card>
      </b-card-group>
    </div>
  </div>
</template>
<script>
export default {
  name: "cardTodo",

  data() {
    return {
      name: "",
      email: "",
      address: "",
      items: [],
    };
  },
  methods: {
    submit() {
      console.log("input" + this.name + " " + this.email + " " + this.address);
      this.items.push({
        name: this.name,
        email: this.email,
        address: this.address,
      });
      this.clear();
    },
    clear(){
        this.name= "",
        this.email = "",
        this.address = ""
    }
  },
};
</script>
