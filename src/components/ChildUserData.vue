<template>
  
        
   <div id = "childDiv" style="float:right ;margin-top:10px;width:50%" >     
<table id = "childTable" class = "table table-striped table-bordered display wrap">     
   <thead>
        <tr>
          <th>ID</th>
          <th>Company</th>
          <th>EyeColor</th>
          <th>Phone</th>
        </tr>
      </thead>
      <tbody>
       <tr v-for="userInfo in userData" :key = "userInfo.index">
         <td>
          {{userInfo.index}}
        </td>
         <td>
          {{userInfo.company}}
        </td>
         <td>
          {{userInfo.eyeColor}}
        </td>
        <td>
          {{userInfo.phone}}
        </td> 
      </tr>
      
      </tbody>
    </table>
    </div>
</template>
<script>

export default {
  name: "ChildUserData",
  props:{
    userData:
    {
      type:Array,
    },
  },
  data() {
      return {
      fields:[
        { key: "index", sortable: true },
        { key: "company", sortable: true },
        { key: "eyeColor", sortable: true },
         { key: "phone", sortable: false }
      ],
  
    }
    }
    
      

  
};
</script>
