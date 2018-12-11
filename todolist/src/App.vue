<template>
  <div id="app">
    <Header> </Header>
    <Todo></Todo>
    <Footer></Footer>
  </div>
</template>

<script>
import Header from './components/header'
import Footer from './components/footer'
import Todo from './components/todo';
export default {
  name: 'App',
  components: {
    Header,
    Footer,
    Todo,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
