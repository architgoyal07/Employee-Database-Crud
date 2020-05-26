<template>
  <div id="app" class="small-container">
    <h1>Employee Database</h1>
    <employee-table v-bind:employee_list="employees"
     @delete:employee="delEmployee" @edit:employee="editEmployee"/>
    <EmployeeForm v-on:add:employee="addNewEmployee"/>
   
    
  </div>
</template>

<script>
import EmployeeTable from './components/EmployeeTable'
import EmployeeForm from '@/components/EmployeeForm'

export default {
  name: 'app',
  components: {
  EmployeeTable,
  EmployeeForm
  },
  data(){
    return{
      employees:[
        {
          id:1,
          name:'Archit Goyal',
          email:'archit@gmail.com'
        },
        {
          id:2,
          name:'Pulkit Aggarwal',
          email:'pulkit@gmail.com'
        }
      ],
     
    }
  },
  methods:{
    addNewEmployee(newEmployee){
    const lastId = this.employees.length>0? this.employees[this.employees.length-1].id:0;
     const newEmployeeId=lastId+1;
     const employee={...newEmployee,newEmployeeId};
      this.employees=[...this.employees,employee];
    
      
    },

    delEmployee(empId){
      
      this.employees = this.employees.filter(employee => employee.id!==empId)
     
    },

    editEmployee(editId,updatedEmployee){
      this.employees = this.employees.map(employee =>
        employee.id === editId ? updatedEmployee: employee
      )
    }
  }
}
</script>

<style  scoped>
.small-container{
  max-width: 800px;
}

 
</style>>

