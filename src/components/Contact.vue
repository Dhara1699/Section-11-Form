<template>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-BmbxuPwQa2lc/FVzBcNJ7UAyJxM6wuqIj61tLrc4wSX0szH/Ev+nYRRuWlolflfl" crossorigin="anonymous">
    <form @submit.prevent="nextPage">
    <header><h2>Contact Details</h2></header>
    <section id="contact">
           <ul>
            <li id="currentadd">    
                <label>CURRENT ADDRESS : {{ currentAdress }} </label>
                <textarea form="userform" rows="5" cols="50" v-model="contacts.enteredCurrentAddress"></textarea><br>
            </li>
            <br>
            <li id="address">    
                <label >PERMANENT ADDRESS : {{ permanentAdress }} </label>
                <textarea form="userform" rows="5" cols="50" v-model="enteredPermanentAddress"></textarea><br>
            </li>
            <br>
            <li id="csc">
                <label>COUNTRY : </label>
               <!-- <input type="text"/><br><br> -->
               <select id="referrer" name="country" v-model="referrer">
                   <option value="india">INDIA</option>
                   <option value="japan">JAPAN</option>
                   <option value="canada">CANADA</option>
               </select><br><br>
                <label>STATE : </label>
              <!--  <input type="text"/><br><br> -->
              <select id="referrer1" name="state" v-model="referrer">
                  <option value="gujarat">GUJARAT</option>
                  <option value="hokkaido">HOKKAIDO</option>
                  <option value="british columbia">BRITISH COLUMBIA</option>
              </select><br><br>
                <label>CITY : </label>
               <!-- <input type="text"/><br><br> -->
               <select id="referrer2" name="city" v-model="referrer">
                   <option value="ahmedabad">AHMEDABAD</option>
                   <option value="sapporo">SAPPORO</option>
                   <option value="vancouver">VANCOUVER</option>
                   
               </select><br><br>
            </li>
            <br>
            <li id="number">
                <label>NUMBER : {{ number }} </label>
                <input type="text" v-model="enteredNumber"/><br><br>
                <label>ALTERNATIVE NUMBER : {{ alternativeNumber }}</label>
                <input type="text" v-model="enteredAlternativeNumber"/><br><br>
            </li>
            <br>
            <li id="email">
                <label>EMAIL ID : {{ emailId }} </label>
                <input type="email" v-model="enteredEmailId"/><br>
            </li>
            <br>  
            <li id="next1">
                <button @click="goToJobDetails">NEXT</button>
                
                    <job v-if="goToJob"></job>
               
            </li>
            </ul>
        </section>
        </form>
</template>

<script>
import Job from './Job.vue';
export default {
    components: {
        Job
    },
    props: {
         currentAdress: {
            type : String,
            required : false,
        },
        permanentAdress: {
            type : String,
            required : true,
        },
        number : {
            type : Number,
            required : true,
        },
        alternativeNumber : {
            type : Number,
            required : false,
        },
        emailId : {
            type : String,
            required : true,
        },
       
    },
    emits: ['next-job'],
      data () {
          return {
              
              goToJob : false,
              contacts : {
              enteredCurrentAddress : '',
              enteredPermanentAddress : '',
              referrer: '',
              enteredNumber : '',
              enteredAlternativeNumber : '',
              enteredEmailId : ''
              }
          };
      },
      methods : {
          submitForm () {
          this.referrer = '';
          },
          goToJobDetails() {
              this.goToJob = !this.goToJob;
          },
          nextPage() {
              this.$emit('next-job', this.contacts);
          },
          
      }

    }
</script>

<style scoped>
* {
  box-sizing: border-box;
}
#form2 {
  left : 450px;
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
#currentadd {
    color: green;
}
#address {
    color: green;
}
#csc {
    color: green;
}
#number {
    color: green;
}
#email {
    color: green;
}
#referrer {
    color: red;
}
#referrer1 {
    color: red;
}
#referrer2 {
    color: red;
}
h2 {
    color: rgb(228, 238, 228);
}
#contact ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
#contact li {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
#next1 button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}
#next1 button:hover,
#next1 button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}
</style>