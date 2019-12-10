<template>
  <div id="app">
   <home>
     <slide></slide>
   </home>
   
    <router-view/>
  </div>
</template>
<script>
import Home from './views/Home'
import Slide from './views/slider'
export default {
  components: {
    Home,
    Slide

  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
}

</style>
