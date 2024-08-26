<template>
  <div>
    <div class="header">
       <h1>TEST 1 RECTANGLE</h1>
    </div>
    <div class="content">
      <div class="DodgerBlueSquare">
        <div >
          <div class="miniSquare DodgerBlueLeft">T</div>
          <div class="miniSquare whiteLeft">S</div>
        </div>
        <div >
          <div class="miniSquare whiteRight">E</div>
          <div class="miniSquare DodgerBlueRight">T</div>
        </div>
      </div>
    </div>
      <div class="bottom">
        <button @click="navigateToAnotherPage" class="btn-1">
          Go to TEST 2
        </button>
      </div>
  </div>

  
</template>

<script setup>
import { useRouter } from 'vue-router'

const router = useRouter()

const navigateToAnotherPage = () => {
  router.push('/test2') // Replace '/another-page' with your target route
}


</script>

<style  scoped>
*{
  font-family: Helvetica, Arial, sans-serif;
  
}
.header {
  display:flex;
  
  margin-bottom:20px;
}
.bottom {
  display:flex;
  margin:20px;
  justify-content: flex-end;
}
.content {
  display:flex;
  justify-content: center;
}
.btn-1 {
  background: black;
  color: white;
  font-size:2rem;
  padding:20px 50px;
  border-radius: 30px;
  transition: all 0.25s ease;
  position:relative;
  cursor: pointer;
}
.btn-1:hover {
  background-color: rgb(106, 105, 105);
}

  .DodgerBlueSquare {
  background: DodgerBlue;
  width: 1600px;
  height: 1600px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  
}

.miniSquare {
  width: 750px;
  height: 750px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 15rem;
  margin: 0;
  box-sizing: border-box;
  position: relative; 
}
.DodgerBlueLeft {
  background: DodgerBlue;
  color: white; 
  position: relative;
  box-shadow: -8px -8px 0 8px black,0 15px 10px -5px rgb(163, 177, 192);;
  z-index: 1;
}
.whiteRight {
  background: white;
  color: grey;
  position: relative;
  box-shadow: 
    8px -8px 0 8px black;
}
.whiteRight::after {
  content: '';
  position: absolute;
  top: 0;
  right:-17px; /* Adjust as needed */
  width: 17px; /* Adjust as needed */
  height: 100%;
  background: DodgerBlue;
  z-index: 1; /* Ensures the right shadow is on top */
}
.whiteLeft {
  background: white;
  color: grey;
  position: relative;
  box-shadow: 
    -8px 8px 0 8px black;
}
.whiteLeft::after {
  content: '';
  position: absolute;
  top: 0;
  left:-17px; /* Adjust as needed */
  width: 17px; /* Adjust as needed */
  height: 100%;
  background: DodgerBlue;
  z-index: 1; /* Ensures the right shadow is on top */
}
.DodgerBlueRight {
   background: DodgerBlue;
  color: white; 
  position: relative;
  box-shadow: 8px 8px 0px 8px black,0 -15px 10px -5px rgb(163, 177, 192);;
  z-index: 2;
}


</style>