<template>
    <div>
        <form>
            <label>Name</label>
            <input type="text" v-model="employee.name">
            <label>Email</label>
            <input type="text" v-model="employee.email">
            <button v-on:click="addEmployee">Add</button>
        </form>
    </div>
</template>

<script>
//import {required,maxLength,minLength,between} from 'vuelidate/lib/validators'

export default {

    name:'EmployeeForm',
    
    data(){
        return{
            employee:{
                
                name:'',
                email:''
            }
        }
    },
   /* validations:{
                name:{
                required,
                minLength:minLength(3),
                maxLength:maxLength(15)
            },
                email:{
                    required,
                    minLength:minLength(10),
                    maxLength:maxLength(29)
                }
    },
    */
    methods:{
        addEmployee(e){
            e.preventDefault()
            this.$emit('add:employee',this.employee)

            this.employee.name ='';
            this.employee.email ='';
        }
    }
}
</script>


<style scoped>
</style>