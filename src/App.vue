<script setup>
import{ref,reactive,computed} from 'vue';
const status=ref(1)


const persperctiveObj  = reactive({
  prespective :100,
  rotateX :0,
  rotateY :0,
  rotateZ :0
});

const change = computed(()=>{
  return{
    transform : `
perspective(${persperctiveObj.prespective}px)
rotateX(${persperctiveObj.rotateX}deg)
rotateY(${persperctiveObj.rotateY}deg)
rotateZ(${persperctiveObj.rotateZ}deg)

    `
  }

})

const reset =()=>
{ persperctiveObj.prespective =100
  persperctiveObj.rotateX =0
  persperctiveObj.rotateY =0
  persperctiveObj.rotateZ =0
} 



</script>

<template>
 <h2>CSS3 Perspective Playground</h2>
    <main>
      <section class="settings">
        <div class="settings-container">
          <label>perspective:{{persperctiveObj.prespective}}px;</label>
          <input type="range" min="0" max="999"  v-model="persperctiveObj.prespective" />

          <label>rotateX:{{persperctiveObj.rotateX}} deg; </label>
          <input type="range" min="-180" max="180" v-model="persperctiveObj.rotateX" />

          <label>rotateY:{{persperctiveObj.rotateY}} deg; </label>
          <input type="range" min="-180" max="180" v-model="persperctiveObj.rotateY" />

          <label>rotateZ:{{persperctiveObj.rotateZ}} deg; </label>
          <input type="range" min="-180" max="180" v-model="persperctiveObj.rotateZ" />

          <button @click.prevent="reset" type="button">Reset</button>
          <button @click="status=1" type="button">Box</button>
          <button @click="status=2" type="button">Triangle</button>
          <button @click="status=3" type="button">Circle</button>
         
       
        </div>
      </section>
      <section class="output">
        <div class="box-container">
          <div v-if="status==1"  class="box" :style="change"></div>
          <div v-if="status==2" class="triangle" :style="change"></div>
          <div v-if="status==3" class="circle"  :style="change"></div>
         
        </div>
      </section>
    </main>
 
</template>

<style scoped>

</style>
