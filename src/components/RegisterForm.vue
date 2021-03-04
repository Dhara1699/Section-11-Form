<template>
<form @submit.prevent="submitData">
    
<personal @next-contact="addPersonal"
:v-for="personal in personals"
:key="personal.id"
:first-name="personal.firstName"
:last-name="personal.lastName"
:gender="personal.egender"
:dob="personal.dateOfBirth"
:hobbies="personal.ehobbies"
:languages="personal.elanguages"></personal>

<contact @next-job="addContact"
:v-for="contact in contacts"
:key="contact.id"
:cur-address="contact.currentAdress"
:per-address="contact.permanentAdress"
:referrer="contact.referrer"
:number="contact.number"
:alt-number="contact.alternativeNumber"
:em-id="contact.emailId"></contact>

<job @submit-form="addJob"
:v-for="job in jobs"
:key="job.id"
:id="job.employeeId"
:ename="job.name"
:cname="job.companyName"
:esalary="job.salary"></job>
</form>
    
</template>

<script>
import Personal from './Personal.vue';
import Contact from './Contact.vue';
import Job from './Job.vue';
export default {
   components: {
       Personal,
       Contact,
       Job
   },
   emits:['add-contant'],
   methods: {
   submitData() {
       this.$emit('add-contant');
   },
   addPersonal(firstname, lastname, gender, dob, hobbies,languages) {
       const newPersonalDetails = {
           firstname : firstname,
           lastname : lastname,
           gender : gender,
           dob :dob,
           hobbies : hobbies,
           languages : languages
       }
       this.personals.push(newPersonalDetails);
   },
   addContact(caddress, paddress, referrer, number, altnumber, eid) {
       const newContactDetails = {
           caddress : caddress,
           paddress : paddress,
           referrer : referrer,
           number : number,
           altnumber :altnumber,
           eid : eid
       }
        this.contacts.push(newContactDetails);

   },
   addJob(id, ename, cname, esalary) {
       const newJobDetails = {
           id : id,
           ename : ename,
           cname : cname,
           esalary : esalary
       };
       this.jobs.push(newJobDetails);
   },
   

}
}
</script>
