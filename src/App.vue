<template>
  <div id="app">
<!--<Users  />  -->
<Navbarku1 />
<Navbarku />
<div class="container">

      <h1 class="mb-4">Daftar Pelanggan</h1> 
        <hr>
      <p> 
        <button class="btn btn-primary" type="button" data-toggle="collapse" data-target="#collapseExample" aria-expanded="false" aria-controls="collapseExample">
        Tambah Pelanggan
        </button>
      </p>

   <!--   <customer-table 
          v-bind:customers='customers' 
          @edit-customer="editCustomer"
           @delete-customer="deleteCustomer"
        />-->

     <Customer v-bind:customers='customers' @edit-customer="editCustomer"    @delete-customer="deleteCustomer" /> 
        <div class="collapse" id="collapseExample">
        <div class="card card-body">
          <h2>Input Data Pelanggan</h2>
          <hr>
        
          <CustomerForm @add-customer="addCustomer"/>

        </div>
      </div>
    </div>
 
  </div>
</template>

<script>

//import Users from './components/Users.vue'
import Customer from './components/Customer.vue'
import CustomerForm from './components/CustomerForm.vue'
import Navbarku1 from './components/Navbarku1.vue';
import Navbarku from './components/Navbarku.vue';

export default {
  name: 'App',
  components: {
    //Users,
    Navbarku1,
    Navbarku,
    Customer,
    CustomerForm

  },
  data() {
    return {
      customers: [
        {
          id: 1,
          name: 'Bambang',
          email: 'bambang@mail.com',
          address: 'Jl.Kenanga',
        },
        {
          id: 2,
          name: 'Dika',
          email: 'dika@mail.com',
          address: 'Jl.Mangga',
        },
        {
          id: 3,
          name: 'Agus',
          email: 'agus@mail.com',
          address: 'Jl.Mataram',
        },
      ],
    }
  },
    methods: {
        addCustomer(customer) {
          this.customers.push(customer);
        },
        editCustomer(id, data) {
          this.customers = this.customers.map(function (customer) { 
            return customer.id === id ? data : customer;
          });
        },
        deleteCustomer(id) {
          this.customers = this.customers.filter(function (customer) { 
            return customer.id !== id;
          });
        }
    }
  
}
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 0px;
}
</style>
