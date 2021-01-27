<template>
<div>
  <h2>User Data App</h2>
  <div id = "parentDiv" style="float:left ;margin-top:10px;width:48%" >
    
    <table id = "parentTable" class = "table table-striped table-bordered display wrap">
      <thead>
        <tr>
          <th>ID</th>
          <th>Name</th>
          <th>Gender</th>
          <th>Email</th>
          <th>Age</th>
        </tr>
      </thead>
      <tbody>
       <tr v-for="user in users" :key = "user.index">
         <td>
          {{user.index}}
        </td>
         <td>
          {{user.name}}
        </td>
         <td>
          {{user.gender}}
        </td>
         <td>
          {{user.email}}
        </td>
        <td>
          {{user.age}}
        </td>
         </tr>
      
      </tbody>
    </table>
    </div> 
    <div id = "child">    
         <ChildUserData :userData = "userData"/> 
    </div>
  <div class="container">
    <line-chart
      :chartdata="chartdata"
      :options="options"/>
  </div>

    </div>
</template>
<script>
import axios from "axios";
import ChildUserData from './ChildUserData.vue';
import Chart from 'chart.js';


   
 

export default {
  extends :Line,
  props:{
    chartdata :{
      type:Object,
      default:null,
    },
    options:{
      type:Object,
    }
  },
  name: "UserFetch",
  components:{ChildUserData},
  data() {
    return {
      users: [],
      userData :[],
     
      msg: "Welcome to Your Vue.js App",
    };
  },
  mounted() {
    //const url = "https://jsonplaceholder.typicode.com/users/";
    const url = "http://www.json-generator.com/api/json/get/bUSQjUafTm?indent=2";

    axios.get(url).then((response) => {
        this.users = response.data;
      for(var i = 0 ; i < this.users.length ; i++)  
    {
/**Creating a subset of data from the users array creating userInfo array and passing it as a prop to child-component */
      var userInfo = this.users[i];
      userInfo.index = this.users[i].index;
      userInfo.eyeColor =  this.users[i].eyeColor;
      userInfo.company =  this.users[i].company;
      userInfo.phone = this.users[i].phone;
      this.userData.push(userInfo);
      this.chartdata = this.users;
      this.renderChart(this.chartdata, this.options)

    }
      }).catch( error => { console.log(error); });
       
   

   
  },
};
</script>




+3
