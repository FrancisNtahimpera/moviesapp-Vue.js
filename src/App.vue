<template>

<header>
  
      <router-link to="/">

        <h1> <span>Vue Movies</span></h1>
      
      </router-link>
    </header>
    
      <router-view/>
 

</template>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family:"Fire Sans" serif;
  &::selection{
    background: transparentize(#428883,0.5);

  }
}
body{
  background: #44cee0;

}
a{
  text-decoration: none;}
  
  
  header{
    display: flex;
    align-items:center ;
    justify-content: center;
    padding: 10px 16px ;
background-color: rgb(173, 113, 126); 
box-shadow: 0px 0px 6px rgba(0, 0, 0, 0.1);
 }

h1 {
  color: white;
  font-size: 28px;

}
</style>
