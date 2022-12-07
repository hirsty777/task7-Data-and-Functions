<template>
  <h2>My Course Goal</h2>
  <!-- Task 1: Output your main course goal with help of the composition API -->
  <!-- Don't hardcode it into the template, instead hardcode it into the JS code -->
  <h3 v-if="isVisible">{{ separateRef }}</h3>
  <h3 v-if="isVisible">{{ refObject.myCorseGoal }}</h3>
  <h3 v-if="isVisible">{{ reactiveObject.myCorseGoal }}</h3>
  <!-- Task 2: Toggle (show/ hide) the goal with help of the button  -->
  <button @click="toogleGoal">{{ showHide }}</button>
  <!-- Task 3: Manage data in three ways -->
  <!-- => Separate refs -->
  <!-- => Ref Object -->
  <!-- => Reactive Object -->
  <!-- Task 4: Also solve the assignment with the Options API -->
  <h2>Options API</h2>
  <h3 v-if="showGoal">{{ myCorse }}</h3>
  <button @click="toogleMyGoal">{{ hideShow }}</button>
</template>

 
<script>
import {ref, reactive, computed} from 'vue';

export default {
  setup(){
    const isVisible = ref(true);

    const separateRef = ref('Learn vue.js(Separate ref)');
    const refObject = ref({myCorseGoal:'Learn vue.js(Ref Object)'});
    const reactiveObject = reactive({myCorseGoal:'Learn vue.js(Reactive Object )'})


    function toogleGoal(){
      isVisible.value = !isVisible.value;
    }

    const showHide = computed(function(){
      if(isVisible.value){
        return 'Hide'
      }else{
         return 'Show'
      }
    }) 
     
    return {  isVisible, separateRef, refObject, reactiveObject, toogleGoal, showHide}
  },


  data(){
      return{
        showGoal:true,
        myCorse:'Learn vue.js'
      }
  },
  methods:{
    toogleMyGoal(){
      this.showGoal = !this.showGoal
    }
  },
  computed:{
    hideShow(){
      if(this.showGoal){
        return 'Hide'
      }else{
        return 'Show'
      }
    }
  }
}
</script>



<style>
html {
  font-family: sans-serif;
}
body {
  margin: 3rem;
  text-align: center;
}
</style>