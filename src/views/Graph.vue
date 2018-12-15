<template>
    <div>
           <bars
            :data="country"
            :gradient="['#ffbe88', '#ff93df']"
            :barWidth="5"
            :growDuration="1">
            </bars>
    </div>
</template>
<script>
import axios from 'axios'
export default {
  name: 'country',
  data(){
      return {
          message:'Final Test ',
          country: [],
          pageSize: 10,
          pageIndex: 1,
          fields: [ 
              {
                  key:'country',
                  sortable : true
              },
              {
                  key:'range',
                  sortable : true
              }
        ],
      }
  },
  mounted(){
      var instance = this
      axios
      .get('https://resttestfinal.herokuapp.com/api/country')
      .then(function(response){
          console.log(response.data.data) 
          instance.country = response.data.data

      })
  }
}
</script>
