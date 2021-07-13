<template>
  <router-view/>
</template>

<style lang="scss">

@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,200;0,300;0,400;0,500;0,600;0,700;1,300;1,400;1,500&family=Nunito:ital,wght@0,200;0,300;0,400;0,600;0,700;0,800;1,300;1,400;1,600&family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;1,100;1,300;1,400;1,500&display=swap');

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  outline: none;
  font-family: 'Montserrat', sans-serif;
}

:root{
  --primary-text-color: rgb(61,100,255);
  --secondary-text-color: rgb(154,158,173);
  --tetiary-text-color: rgb(204,209,225);
  --quatenary-text-color: rgb(234,237,244);
  --primary-bg: rgb(25,32,57);
  --secondary-bg: rgb(30,39,70);
  --tetiary-bg: rgb(33,43,79);
  --quaternary-bg: rgb(54,63,94);
  --quinary-bg: rgb(46,52,73);
}

body {
  background-color: var(--primary-bg);
}

a {
  text-decoration: none;
}

ul,
li {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

h1,
h2 {
  font-family: "Nunito", sans-serif;
}

h3,
h4 {
  font-family: "Montserrat", sans-serif;
}

p,
a,
span,
button,
input,
select,
option,
ul,
li,
table,
td,
tr,
th,
tbody,
thead,
label,
textarea,
::placeholder {
  font-family: "Roboto", sans-serif;
}

</style>
