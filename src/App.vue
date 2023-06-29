<template>
  <div>

    <div class="session">
    <glass/>
    </div>


  </div>
</template>

<script>
import glass from "./components/glass.vue"
export default {
  components:{
    glass
  }
}
</script>

<style  scoped>


.session{

display: flex;
justify-content: center;
justify-items: center;
margin-top: 70px

}


</style>