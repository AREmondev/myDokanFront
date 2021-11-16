<template>
    <client-only>
        <div class="py-5">
            <Search/>
            <div class="input-group mb-3">
                <input @keyup="search" v-model="search_text" type="search" class="form-control p-2" aria-label="Text input with dropdown button">
                <button class="btn btn-outline-secondary" type="button" id="inputGroupFileAddon04">Search</button>
            </div>
            <ul class="list-group" v-if="filterData.length > 0">
                <li class="list-group-item mb-5">
                    <h4>Image</h4>
                    <h4>Name</h4>
                    <h4>Village</h4>
                    <h4>Total Due</h4>
                    <h4>Action</h4>
                </li>
                <li class="list-group-item" v-for="customer in filterData" :key="customer.id">
                    <img src="https://images.rawpixel.com/image_png_800/czNmcy1wcml2YXRlL3Jhd3BpeGVsX2ltYWdlcy93ZWJzaXRlX2NvbnRlbnQvdjc5MS10YW5nLTM1LnBuZw.png?s=aLxshBxLcykO2UAnr6F0Nzhqtdx6iR6UuKi4bFSTzC8" alt="">
                    <a class="name" href="#">{{customer.name}}</a>
                    <h5>{{customer.village}}</h5>
                    <h5 class="number">{{customer.total_due}}</h5>
                    <nuxt-link :to="'/order/persons?name='+customer.id" class="number">Make Order</nuxt-link>
                </li>
            </ul>
        </div>
    </client-only>
</template>

<script>
import Search from "~/components/search/search.vue"
export default {
    components: {Search},
    props: {
        customers: {
            type: Array,
            default: [],
            required: true,
        }
    },
    data(){
        return {
             search_text: '',
             filterData: this.$props.customers
        }
    },
    created() {
    },
    methods:{
        search(){
            this.filterData = this.$props.customers.filter(data => data.name.toLowerCase().includes(this.search_text.toLowerCase()))
        }
    }
}
</script>

<style>
.list-group-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 0.7rem;
    border: none;
    background-color: #ffffff;
    box-shadow: 0 0 15px #fff;
    border-radius: 0.3rem;
}
li.list-group-item img {
    height: 60px !important;
    min-width: 60px !important;
    width: 60px !important;
    border-radius: 60px;
}
a.name {
    font-size: 1.8rem;
    color: rgb(15, 15, 15);
    text-decoration: none;
}
</style>