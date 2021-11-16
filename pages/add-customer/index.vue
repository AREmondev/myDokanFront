<template>
  <div  class="container  py-5 ">
    <h1>Add Customer</h1>
    <form class="w-100  my-5">
        <div class="form-row row">
        <div class="form-group col-md-6 col-xl-4">
            <label for="inputEmail4">Name</label>
            <input v-model="name"  type="text" class="form-control" >
        </div>
        <div class="form-group col-md-6 col-xl-4">
            <label for="inputEmail4">Village</label>
            <input v-model="village"  type="text" class="form-control" >
        </div>
        <div class="form-group col-md-6 col-xl-4">
            <label for="inputEmail4">Phone</label>
            <input v-model="phone"  type="text"  class="form-control" >
        </div>
        <div class="form-group col-md-6 col-xl-4">
            <label for="inputEmail4">Due</label>
            <input v-model="due"  type="text"  class="form-control" >
        </div>
        <button @click.prevent="makeCustomer" class="btn btn-primary w-75 text-center my-2 mx-auto">Submit</button>
    </div>
</form>
  </div>

</template>

<script>
import Main from "~/components/home/main.vue"
import {API_URL} from "~/plugins/api"
export default {
  components: {Main},
  data(){
    return {
      phone: '',
      name: '',
      due: '',
      village: '',
    }
  },
  created() {
  },
  methods: {
    makeCustomer(){
      if(process.browser){
          let url = API_URL("customers/");
          let token = "Bearer " + localStorage.getItem("token");
          let data = {
              'name': this.name,
              'phone': parseInt(this.phone),
              'village': this.village,
              'Total_due': parseInt(this.due),
              'PreviousDue':  parseInt(this.due),
              }
              console.log(data)
          this.$axios.post(url, data, {headers: {Authorization: token}}).then(response => {
              console.log(response)
            // if(response.status == 200){
            //   this.orders = response.data.reverse();
            // }
          }).catch(err => console.log(err));
      }
    },
  }
}
</script>
