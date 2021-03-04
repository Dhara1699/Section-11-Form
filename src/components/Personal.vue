<template>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-BmbxuPwQa2lc/FVzBcNJ7UAyJxM6wuqIj61tLrc4wSX0szH/Ev+nYRRuWlolflfl" crossorigin="anonymous">
    <form @submit.prevent="nextPage">
    <header><h2>Personal Details</h2></header>
    <section id="personal">
        <ul>
            <li id="firstname" class="formControl" :class="{invalid: userNameValidity === 'invalid'}">   
                <label>FIRST NAME : {{ firstName }} </label>
                <input type="text" name="firstName" v-model.trim="enteredFirstname" @blur="validateInput"/><br><br>
                <p v-if="userNameValidity === 'invalid'">Please enter valid name!</p>
                
            </li >
            <li id="lastname">
                <label>LAST NAME : {{ lastName }} </label>
                <input type="text" name="lastName" v-model="enteredLastname"/><br>
            </li>
                <br>
            <li id="gender">
                <label>GENDER : </label><br>
                <input type="radio" id="male" name="gender" value="male" v-model="gender"/>
                <label for="male">Male</label><br>
                <input type="radio" id="female" name="gender" value="female"  v-model="gender"/>
                <label for="female">Female</label><br>
                <input type="radio" id="other" name="gender" value="other"  v-model="gender"/>
                <label for="other">Other</label><br>
            </li>
                <br>
            <li id="dob">
                <label>DATE OF BIRTH : {{ dateOfBirth }}</label>
                <input type="date" name="begin" placeholder="dd-mm-yyyy" value="" min="1995-01-01" max="2020-12-30"><br> 
            </li>
            <br>
            <li id="hobbies">
                <label>HOBBIES : {{ ehobbies }} </label><br>
                <input type="checkbox" name="hobbies" value="singing" v-model="hobbies"/>SINGING<br>
                <input type="checkbox" name="hobbies" value="football" v-model="hobbies"/>FOOTBALL<br>
                <input type="checkbox" name="hobbies" value="reading" v-model="hobbies"/>READING<br>
                <input type="checkbox" name="hobbies" value="cricket" v-model="hobbies"/>CRICKET<br>
            </li>
            <br>
            <li id="languages">
                <label>LANGUAGES : {{ elanguages }} </label><br>
                <input type="checkbox" name="languages" value="english" v-model="languages"/>
                <label for="english">ENGLISH</label><br>
                <input type="checkbox" name="languages" value="hindi" v-model="languages"/>
                <label for="hindi">HINDI</label><br>
                <input type="checkbox" name="languages" value="gujarati" v-model="languages"/>
                <label for="gujarati">GUJARATI</label><br>
            </li>
            <br>
            <li id="next1">
                <button @click="goToContactDetails">NEXT</button>
                
                    <contact v-if="goToContact"> </contact>
                
            </li>
        </ul>    
        </section>
    </form>
</template>

<script>
    import Contact from './Contact.vue';
    export default {
        components : {
            Contact
        },
        props : {
             firstName: {
            type: String,
            required : true,
        },
        lastName: {
            type: String,
            required : true,
        },
        egender: {
            type: String,
            required : true
        },
        dateOfBirth: {
            type: Date,
            required : true,
        },
        ehobbies: {
            type : String,
            required : true
        },
        elanguages : {
            type : String,
            required : true
        }
        },
        emits : ['next-contact'],
         data () {
            return {
               firstname : '',
               lastname : '',  
               userNameValidity : 'pending' ,
               goToContact : false,
               personals : {
               enteredFirstName : '',
               enteredLastName : '',
               gender : null,
               enteredDateOfBirth : null,
               hobbies : [],
               languages : [],
            }
         };
     },
     methods : {
        submitForm () {
        this.firstname = '';
        this.lastname = '';
        this.gender = null;
        this.hobbies = [];
        this.languages = [];
      },
      validateInput() {
          if(this.firstname === '') {
              this.userNameValidity = 'invalid';
          }else {
              this.userNameValidity = 'valid';
          }
      },
      goToContactDetails() {
          this.goToContact = !this.goToContact;
      },
      nextPage() {
          this.$emit('next-contact', this.personals);
      }
     }
    }
</script>

<style scoped>
* {
  box-sizing: border-box;
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
.formControl.invalid input {
    border-color: red;
}
.formControl.invalid label {
    color: red;
}
#name {
   color:green;
}
#gender {
    color: green;
}
#dob {
    color: green;
}
#hobbies {
   color: green; 
}
#languages {
    color: green;
}
#personal ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
#personal li {
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