<template>
  <div  class="container">
    <Main :customers="customers"/>
  </div>

</template>

<script>
import Main from "~/components/home/main.vue"
import {API_URL} from "~/plugins/api"
export default {
  components: {Main},
  data(){
    return {
      customers: [],
    }
  },
  created() {
    this.getUser()
  },
  methods: {
    getUser(){
      if(process.browser){
          let url = API_URL("customers/");
           let token = "Bearer " + localStorage.getItem("token")
           console.log(token)
          this.$axios.get(url, {headers: {Authorization: token}}).then(response => {
            if(response.status == 200){
              this.customers = response.data;
            }
          }).catch(err => console.log(err));
      }
    }
  }
}
</script>
