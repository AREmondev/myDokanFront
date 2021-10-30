<template>
  <div  class="container">
    <h1>Orders</h1>
    <button @click="makeOrder">makeOrder</button>
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
    this.getOrder()
  },
  methods: {
    getOrder(){
      if(process.browser){
          let url = API_URL("orders/?qyery=emon&id=12");
          this.$axios.get(url).then(response => {
              console.log(response)
            if(response.status == 200){
              this.customers = response.data;
            }
          }).catch(err => console.log(err));
      }
    },
    makeOrder(){
      if(process.browser){
          let url = API_URL("orders/");
          let data =  {
        "id": 1,
        "due": 100,
        "total": 200,
        "payment": 100,
        "customer": null,
        "published_at": "2021-10-16T04:21:28.717Z",
        "created_at": "2021-10-16T04:20:48.519Z",
        "updated_at": "2021-10-16T12:29:58.176Z",
        "products": [
            {
                "id": 1,
                "name": "Amister Top ",
                "recived": "2021-10-16",
                "expire": null,
                "expired": false,
                "stock": 15,
                "sell": 8,
                "total_recived": 23,
                "price": 1700,
                "published_at": "2021-10-16T04:21:54.830Z",
                "created_at": "2021-10-16T03:51:46.704Z",
                "updated_at": "2021-10-16T13:15:52.298Z",
                "images": [
                    {
                        "id": 1,
                        "name": "emon.jpg",
                        "alternativeText": "",
                        "caption": "",
                        "width": 1152,
                        "height": 2048,
                        "formats": {
                            "thumbnail": {
                                "name": "thumbnail_emon.jpg",
                                "hash": "thumbnail_emon_d14602f099",
                                "ext": ".jpg",
                                "mime": "image/jpeg",
                                "width": 88,
                                "height": 156,
                                "size": 4.92,
                                "path": null,
                                "url": "/uploads/thumbnail_emon_d14602f099.jpg"
                            },
                            "large": {
                                "name": "large_emon.jpg",
                                "hash": "large_emon_d14602f099",
                                "ext": ".jpg",
                                "mime": "image/jpeg",
                                "width": 563,
                                "height": 1000,
                                "size": 120.44,
                                "path": null,
                                "url": "/uploads/large_emon_d14602f099.jpg"
                            },
                            "medium": {
                                "name": "medium_emon.jpg",
                                "hash": "medium_emon_d14602f099",
                                "ext": ".jpg",
                                "mime": "image/jpeg",
                                "width": 422,
                                "height": 750,
                                "size": 72.11,
                                "path": null,
                                "url": "/uploads/medium_emon_d14602f099.jpg"
                            },
                            "small": {
                                "name": "small_emon.jpg",
                                "hash": "small_emon_d14602f099",
                                "ext": ".jpg",
                                "mime": "image/jpeg",
                                "width": 281,
                                "height": 500,
                                "size": 33.83,
                                "path": null,
                                "url": "/uploads/small_emon_d14602f099.jpg"
                            }
                        },
                        "hash": "emon_d14602f099",
                        "ext": ".jpg",
                        "mime": "image/jpeg",
                        "size": 408.8,
                        "url": "/uploads/emon_d14602f099.jpg",
                        "previewUrl": null,
                        "provider": "local",
                        "provider_metadata": null,
                        "created_at": "2021-10-16T03:32:43.510Z",
                        "updated_at": "2021-10-16T03:32:43.531Z"
                    }
                ]
            }
        ]
    }
          this.$axios.post(url, data).then(response => {
              console.log(response)
            if(response.status == 200){
              this.customers = response.data;
            }
          }).catch(err => console.log(err));
      }
    }
  }
}
</script>
