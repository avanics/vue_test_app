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
    <canvas id="my-chart" width="500" height="300"></canvas>
    </div>
</template>
<script>
import axios from "axios";
import ChildUserData from './ChildUserData.vue';
import Chart from 'chart.js'
   
 

export default {
  name: "UserFetch",
  components:{ChildUserData },
  data() {
    return {
      users: [],
      userData :[],
      countA : 0,
      countB : 0,
      countC:0,
      countD:0,
      countE:0,
      msg: "Welcome to Your Vue.js App",
    };
  },
  mounted() {
    //const url = "https://jsonplaceholder.typicode.com/users/";
    //const url = "http://www.json-generator.com/api/json/get/bUSQjUafTm?indent=2";
    const url = "http://www.json-generator.com/api/json/get/bTTvRHFEqG?indent=2";
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
      if(userInfo.age >= 16 && userInfo.age <= 20)
        this.countA++;
      if(userInfo.age >= 21 && userInfo.age <= 25)
        this.countB++;
      if(userInfo.age >= 26 && userInfo.age <= 30)
            this.countC++;
      if(userInfo.age >= 31 && userInfo.age <= 35)
            this.countD++;
      if(userInfo.age >= 36 && userInfo.age <= 40)
            this.countE++;




    }
    new Chart(document.getElementById('my-chart'), {
  type: 'line',
  data: {
    labels: ['16-20', '21-25', '26-30', '31-35', '36-40'],
    datasets: [
      {
        label: 'Users Age',
        data: [this.countA, this.countB, this.countC, this.countD, this.countE]
      }
    ]
  }
});
      }).catch( error => { console.log(error); });
       
   

   
  },
  methods:
  {
    displayChart()
    {
      this.lineChartData = {
        labels:[16-20 ,21-25, 26-30, 31-35,36-40],
        datasets:[
          {
          label:"Age Group",
          backgroundColor :"#f87979",
          data:['4', '3','3','5','2']
          }
        ]
      }
    }
  }
};
</script>




+3
