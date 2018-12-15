<template>
    <div>
            <h1>Customer List</h1>
            <b-table striped hover 
        :items="customer" 
        :fields="fields" 
        :per-page="pageSize" 
        :current-page="pageIndex"></b-table>
        <b-pagination size="md" :total-rows="customer.length" v-model="pageIndex" :per-page="pageSize">
    </b-pagination>
    </div>
</template>
<script>
import axios from 'axios'
export default {
  name: 'customer',
  data(){
      return {
          message:'Final Test',
          customer: [],
          pageSize: 10,
          pageIndex: 1,
          fields: [ 
              {
                  key:'customer_id',
                  sortable : true
              },
              {
                  key:'company_name',
                  sortable : true
              },
              {
                  key:'phone',
                  sortable : true,
                  variant: 'danger'
              },
        ],
      }
  },
  mounted(){
      var instance = this
      axios
      .get('https://resttestfinal.herokuapp.com/api/customer')
      .then(function(response){
          console.log(response.data.data) 
          instance.customer = response.data.data
      })
  }
}
</script>
