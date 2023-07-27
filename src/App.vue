<script setup>
import{ref,reactive,computed} from 'vue';
const status=ref(1)


const persperctiveObj  = reactive({
  prespective :100,
  rotateX :0,
  rotateY :0,
  rotateZ :0,
  transformOriginX: "center",
  transformOriginY: "center",
 
});






const change = computed(()=>{
  return{
    transform : `
perspective(${persperctiveObj.prespective}px)
rotateX(${persperctiveObj.rotateX}deg)
rotateY(${persperctiveObj.rotateY}deg)
rotateZ(${persperctiveObj.rotateZ}deg)


    `,
    transformOrigin:`${persperctiveObj.transformOriginX} ${persperctiveObj.transformOriginY}`

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
    
      <div class="radioButton">
      <label >
          transform-origin: {{persperctiveObj.transformOriginX}} {{persperctiveObj.transformOriginY}}<br>
          <div class="transform-origin-radio-buttons">
            <div class="transform-origin-x">
              <label for="t-left">
                <input type="radio" name="transform-left" value="left" v-model="persperctiveObj.transformOriginX" id="t-left" />
                 left
              </label>
              <br>
              <label for="t-right">
                <input type="radio" name="transform-left" value="right" v-model="persperctiveObj.transformOriginX" id="t-right" /> right
              </label>
              <br>
              <label for="t-center">
                <input type="radio"  name="transform-left" value="center" v-model="persperctiveObj.transformOriginX" id="t-center" /> center
              </label>
            </div>

            <div class="transform-origin-y">
              <label for="t-top">
                <input type="radio" name="transform-right" value="top" v-model="persperctiveObj.transformOriginY" id="t-top" />
                 top
              </label>
              <br>
              <label for="t-bottom">
                <input type="radio" name="transform-right" value="bottom" v-model="persperctiveObj.transformOriginY" id="t-bottom" /> bottom
              </label>
              <br>
              <label for="t-center2">
                <input type="radio" name="transform-right" value="center" v-model="persperctiveObj.transformOriginY" id="t-center2" /> center
              </label>
            </div>
          </div>

        </label>
      </div>
 
</template>

<style scoped>

</style>
