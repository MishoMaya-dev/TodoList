<template>
  <div id="app">
    <h1>ToDo Application</h1>
    <hr>
    <router-view />
  </div>
</template>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 600px;
  margin: 60px auto 0 auto;
}
* {
  box-sizing: border-box;
}
hr {
  margin: 0 0 20px 0;
}
  select {
    margin-bottom: 20px;
    width: 50%;
    height: 25px
  }
</style>
