<template>
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-BmbxuPwQa2lc/FVzBcNJ7UAyJxM6wuqIj61tLrc4wSX0szH/Ev+nYRRuWlolflfl" crossorigin="anonymous">

  <Nav></Nav>
    <header><h1>Registration Form</h1></header>
    <form>
      <ul>
      <personal></personal>
      </ul>
    </form>
</template>

<script>
import Personal from './components/Personal.vue';
import Nav from './components/Nav.vue';

export default {
 // components: { Personal, Contact, Job },
    components : {
        Personal,
        Nav,
    },
    methods : {
      name: 'app',
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
  background-color: #779e0a;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}
h1{
    color: rgb(216, 209, 207);
}

</style>