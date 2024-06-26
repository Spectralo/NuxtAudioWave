<template>
  <div class="container" @click="ShowThemes()">
    <div v-for="(height) in barheights" class="bar" :style="{'--bar-height': height.value+'%'}"></div>
  </div>
  <div class="containerbutton">
    <Icon name="mdi:color" class="icon" size="3vw" @click="ShowThemes()"/>
  </div>
  <div class="containerthemes" :style="{'visibility': hidden }">
    <ul class="themelist">
      <li class="green" @click="ChangeTheme('green')">Green</li>
      <li class="orange" @click="ChangeTheme('orange')">Orange</li>
      <li class="blue" @click="ChangeTheme('blue')">Blue</li>
      <li class="yellow" @click="ChangeTheme('yellow')">Yellow</li>
      <li class="pink" @click="ChangeTheme('pink')">Pink</li>
      <p>Bars:</p>
      <input class="input" type="number"  min="2" max=""></input>
    </ul>
</div>
</template>

<script lang="js" setup>
import { onMounted } from 'vue';

let hidden = "hidden"
let barnum = 20
let barheights = []

function ShowThemes() {
  if (hidden == "hidden") {
    hidden = "visible"
  } else {
    hidden = "hidden"
  }
}

for (let i = 0; i < barnum; i++) {
  barheights.push(ref(0))
}

function ChangeTheme(color) {
  let COLORS = {
    green: "#9ccfd8",
    orange: "#ea9a97",
    blue: "#3e8fb0",
    yellow: "#f6c177",
    pink: "#eb6f92"
  }
  document.documentElement.style.setProperty('--bar-color', COLORS[color])
}

onMounted(() => {
  // Defining barheights list

  navigator.mediaDevices
    .getUserMedia({ audio: true })
    .then((MediaStream) => {
      const audioCtx = new AudioContext();
      const source = audioCtx.createMediaStreamSource(MediaStream);
      const analyser = audioCtx.createAnalyser();
      source.connect(analyser);
      const bufferLength = barnum
      const dataArray = new Uint8Array(bufferLength);
      getAudio()
      setInterval(() => {
        barheights.forEach((bar , index) => {
          const currentHeight = bar.value
          const targetHeight = (dataArray[index]-118) / 11 * 100
          const transitionSpeed = 0.01
          const interpolatedHeight = currentHeight + (targetHeight - currentHeight) * transitionSpeed;
          bar.value = interpolatedHeight
          })
        console.log(barheights)
      }, 1)
      async function getAudio() {
        setInterval(() => {
          analyser.getByteTimeDomainData(dataArray);
        }, 100)
      }
    })
});


</script>



<style>
:root {
  --bar-color: #f6c177;
  --background-color: #1f1d2e;
  --bar-background-color: #191724;
}
body {
  background-color: #1f1d2e;
}
.bar {
  background: linear-gradient(
    to bottom, 
    #191724,
    #191724 var(--bar-height),
    var(--bar-color) var(--bar-height),
    var(--bar-color)
  );
  height: 80vh;
  width: 3vw;
}

.pink {
  color: #eb6f92
}

.green {
  color: #9ccfd8
}

.blue {
  color: #3e8fb0
}
.orange {
  color: #ea9a97
}
.yellow {
  color: #f6c177
}

.icon {
  color: var(--bar-color);
  position: absolute;
  top: 2vh;
  right: 1vw;
}

.containerthemes {
  background-color: var(--bar-background-color);
  color: var(--bar-color);
  border-radius: 20px;
  position: absolute;
  top: 8vh;
  right: 1vw;
  width: fit-content;
}
.themelist {
  list-style-type: none;
  font-family: 'Courier New', Courier, monospace;
  font-size: 1.5vw;
  margin: 0px;
  padding-left: 0px;
}
li {
  padding: 10px;
  cursor: pointer;
}
li:hover {
  background-color: var(--bar-color);
  color: var(--background-color);
}


.container {
  display: flex;
  justify-content: space-around;
  align-items: center;
  height: 100vh;
  margin-left: 5vw;
  margin-right: 5vw;
}

</style>