<template>
<nav>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-BmbxuPwQa2lc/FVzBcNJ7UAyJxM6wuqIj61tLrc4wSX0szH/Ev+nYRRuWlolflfl" crossorigin="anonymous">
  <div class="nav nav-tabs" id="nav-tab" role="tablist">
     <li> 
    <button class="nav-link active" id="nav-personal-tab" type="button" role="tab" aria-controls="nav-personal" aria-selected="true" >Personal Details</button>
     </li>
     <li>
    <button class="nav-link" id="nav-contact-tab" type="button" role="tab" aria-controls="nav-contact" aria-selected="true">Contact Details</button>
     </li>
     <li>
    <button class="nav-link" id="nav-job-tab" type="button" role="tab" aria-controls="nav-job" aria-selected="true">Job Details</button>
    </li>
  </div>
</nav>
</template>

<style scoped>
#nav-tab {
    background-color: rgb(209, 194, 194);
    
} 
#nav-personal-tab,
#nav-contact-tab,
#nav-job-tab :active {
   border-block-color : green;
}

#nav-tab div {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  color: green;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
#nav-tab button :hover,
#nav-tab button :active {
    background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(219, 202, 202, 0.26);
}
</style>