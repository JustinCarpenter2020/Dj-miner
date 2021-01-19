<template>
<header class="container-fluid">
  <div class="text-center" id="title">
  <h1>Mix <span id="offset">Miner</span> yo</h1>
  <h2 class="pink"> <u>Crowd Influence Meter: {{ state.count }}</u></h2>
  </div>
</header>
<body class="continer-fluid">
  <div class="row">
    <div class="col-2">
      <button class="btn little animate-flicker"></button>
    </div>
  </div>
  <div class="row records align-self-center">
    <div class="col-6 text-center">
  <img @click="state.count += state.clickCount" class="forward" src="https://simg.nicepng.com/png/small/18-188232_vinyl-record-drawing-at-getdrawings-record-clip-art.png">
    </div>
    <div class="col-6 text-center">
  <img @click="state.count += state.clickCount" class="reverse" src="https://simg.nicepng.com/png/small/18-188232_vinyl-record-drawing-at-getdrawings-record-clip-art.png">
    </div>
  </div>
</body>

<footer class="container-fluid">
  <div class="row justify-content-between end">
    <button class="btn btn-outline btn-info circle">
    </button>
    <div>
       <button :disabled ="state.count < upgrade.cost" @click="state.count -= upgrade.cost, state.clickCount += upgrade.multiplier" class="btn btn-outline btn-danger" v-for="upgrade in state.upgrades"
      :key="upgrade.name">
       {{upgrade.name}} | {{upgrade.cost}}
    </button>
    </div>
    </div>
</footer>
</template>








<script>
import { computed, reactive } from 'vue'
export default {
  setup() {
    const state = reactive({
      count: 0,
      clickCount: 1,
      upgrades: [{
        name: "Hit a drop",
        cost: 500,
        multiplier: 10
      }, {
        name: "Increase base",
        cost: 20,
        multiplier: 5
      }]
    })
    return {
      state,

    }
  }
}
</script>




<style>

body {
  background-color: #3f3636;
}
html, body {
    max-width: 100%;
    overflow-x: hidden;
    overflow-y: hidden;
}

.forward{
   animation-name: spin;
  animation-duration: 5000ms;
  animation-iteration-count: infinite;
  animation-timing-function: linear; 
  border-radius: 50%;
}

.reverse{
  animation-name: spin2;
    animation-duration: 7000ms;
  animation-iteration-count: infinite;
  animation-timing-function: linear; 
  border-radius: 50%;
}

@keyframes spin {
    from {
        transform:rotate(0deg);
    }
    to {
        transform:rotate(360deg);
    }
}

@keyframes spin2 {
    from {
      transform:rotate(360deg);
    }
    to {
        transform:rotate(0deg);
    }
}

.progress-bar{
  max-width: 50%;
}

.circle{
  border-radius: 50%;
  width: 80px;
  height: 80px;
}

.end{
  position: absolute;
  bottom: 0;
  width: 100%;
}




.little{
  border-radius: 50%;
  width: 30px;
  height: 30px;
  background-color: rgb(187, 17, 17);
  margin-left: 8px;
  pointer-events: none;
}

#title{
   position:absolute;
  border:5px solid #0c6bb9;
  width:300px;
  top:150px;
  border-radius:20px;
  left:50%;
  margin: -50px 0 0 -150px;
  animation: border-flicker 10s linear infinite;
}
h1 {
  color:rgb(4, 217, 255);
  /* font-family: 'Raleway', sans-serif; */
  font-size:64px;
  letter-spacing:10px;
  animation: text-flicker 12s linear infinite;
}
#offset {
  animation: letter-flicker 10s linear infinite;
}

.pink{
  color: #F066F2;
  text-shadow: 2px 2px black;
}












@keyframes text-flicker {
  0% {
    opacity:0.1;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1);
  }
  
  2% {
    opacity:1;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1);
  }
  8% {
    opacity:0.1;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1);
  }
  9% {
    opacity:1;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1);
  }
  12% {
    opacity:0.1;
    text-shadow: 0px 0px rgba(4, 217, 255,1);
  }
  20% {
    opacity:1;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1)
  }
  25% {
    opacity:0.3;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1)
  }
  30% {
    opacity:1;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1)
  }
  
  70% {
    opacity:0.7;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1)
  }
  
  72% {
    opacity:0.2;
    text-shadow:0px 0px 29px rgba(4, 217, 255,1)
  }
  
  77% {
    opacity:.9;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1)
  }
  100% {
    opacity:.9;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1)
  }
}

@keyframes border-flicker {
  0% {
    opacity:0.1;
    -webkit-box-shadow: 0px 0px 78px 4px rgba(16,134,232,0.73);
-moz-box-shadow: 0px 0px 78px 4px rgba(16,134,232,0.73);
box-shadow: 0px 0px 78px 4px rgba(16,134,232,0.73);
  }
  2% {
    opacity:1;
    -webkit-box-shadow: 0px 0px 78px 4px rgba(16,134,232,0.73);
-moz-box-shadow: 0px 0px 78px 4px rgba(16,134,232,0.73);
box-shadow: 0px 0px 78px 4px rgba(16,134,232,0.73);
  }
  4% {
    opacity:0.1;
    -webkit-box-shadow: 0px 0px 78px 4px rgba(16,134,232,0.73);
-moz-box-shadow: 0px 0px 78px 4px rgba(16,134,232,0.73);
box-shadow: 0px 0px 78px 4px rgba(16,134,232,0.73);
  }
  
  8% {
    opacity:1;
    -webkit-box-shadow: 0px 0px 78px 4px rgba(16,134,232,0.73);
-moz-box-shadow: 0px 0px 78px 4px rgba(16,134,232,0.73);
box-shadow: 0px 0px 78px 4px rgba(16,134,232,0.73);
  }
  70% {
    opacity:0.7;
    -webkit-box-shadow: 0px 0px 78px 4px rgba(16,134,232,0.73);
-moz-box-shadow: 0px 0px 78px 4px rgba(16,134,232,0.73);
box-shadow: 0px 0px 78px 4px rgba(16,134,232,0.73);
  }
  100% {
    opacity:1;
    -webkit-box-shadow: 0px 0px 78px 4px rgba(16,134,232,0.73);
-moz-box-shadow: 0px 0px 78px 4px rgba(16,134,232,0.73);
box-shadow: 0px 0px 78px 4px rgba(16,134,232,0.73);
  }
}

@keyframes letter-flicker {
  0% {
    opacity:0.1;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1);
  }
  2% {
    opacity:0.1;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1);
  }
  4% {
    opacity:1;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1);
  }
  
  
  19% {
    opacity:1;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1);
  }
  21% {
    opacity:0.1;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1);
  }
  23% {
    opacity:1;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1);
  }
  
  80% {
    opacity:1;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1);
  }
  83% {
    opacity:0.4;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1);
  }
  87% {
    opacity:1;
    text-shadow: 0px 0px 29px rgba(4, 217, 255,1);
  }
}
@keyframes flickerAnimation {
  0%   { background-color:rgb(187, 17, 17); }
  50%  { background-color:rgb(240, 3, 3); }
  100% { background-color:rgb(187, 17, 17); }
}
</style>