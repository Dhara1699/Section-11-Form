<template>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-BmbxuPwQa2lc/FVzBcNJ7UAyJxM6wuqIj61tLrc4wSX0szH/Ev+nYRRuWlolflfl" crossorigin="anonymous">
  <form @submit.prevent="submitData">
    <header><h2>Job Details</h2></header>
    <section id="job">
            <ul>
            <li id="employeeid">
                <label>EMPLOYEE ID :  </label>
                <input type="text" v-model="enteredEmployeeId"/><br>
            </li>
            <br>
            <li id="name">
                <label>NAME :  </label>
                <input type="text" name="userName" v-model="enteredEmployeeName"/><br>
            </li>
            <br>
            <li id="companyname">
                <label>COMPANY NAME :  </label>
                <input type="text" v-model="enteredCompanyName"/><br>
            </li>
            <br>
            <li id="salary">
                <label>SALARY : </label>
                <input type="text" v-model="enteredSalary"/><br>
            </li>
            </ul>
            <br>  
            <ul id="submit" >
            <li>
                <button @click="submitData">SUBMIT</button>
                <register-form v-if="submitDetails"></register-form>
            </li>
            </ul> 
        </section>  
  </form> 
</template>

<script>
import RegisterForm from './RegisterForm.vue'
export default {
  components: {
    RegisterForm
  },
  props: {
    employeeId : {
            type : Number,
            required : true,
        },
        name : {
            type : String,
            required : true,
        },
        companyName : {
            type : String,
            required : true,
        },
        salary : {
            type : Number,
            required : true,
        }
  },
  emits: ['submit-form'],
data() {
  return {
    submitDetails : false,
    jobs : {
    enteredEmployeeId : '',
    enteredEmployeeName : '',
    enteredCompanyName : '',
    enteredSalary : ''
    }
  };
},
methods: {
  submitData() {
    this.$emit('submit-form', this.jobs);
    this.submitDetails = !this.submitDetails;
  },  
}
}
</script>

<style scoped>
* {
  box-sizing: border-box;
  box-shadow: blue;
}
header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
#employeeid {
    color: green;
    box-sizing: border-box;
}
#name {
    color: green;
}
#companyname {
    color: green;
}
#salary {
    color: green;
}
h2 {
    color: rgb(232, 238, 232);
}
#job ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
#job li {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
#submit button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}
#submit button:hover,
#submit button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}
</style>