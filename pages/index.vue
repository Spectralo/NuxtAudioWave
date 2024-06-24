<template>
  <div class="container">
    <div class="bar" :style="{'--bar-height': bar1height + '%'}"></div>
    <div class="bar" :style="{'--bar-height': bar2height + '%'}"></div>
    <div class="bar" :style="{'--bar-height': bar3height + '%'}"></div>
    <div class="bar" :style="{'--bar-height': bar4height + '%'}"></div>
    <div class="bar" :style="{'--bar-height': bar5height + '%'}"></div> 
    <div class="bar" :style="{'--bar-height': bar6height + '%'}"></div> 
    <div class="bar" :style="{'--bar-height': bar7height + '%'}"></div>  
    <div class="bar" :style="{'--bar-height': bar8height + '%'}"></div>  
    <div class="bar" :style="{'--bar-height': bar9height + '%'}"></div>  
    <div class="bar" :style="{'--bar-height': bar10height + '%'}"></div>
    <div class="bar" :style="{'--bar-height': bar11height + '%'}"></div>
    <div class="bar" :style="{'--bar-height': bar12height + '%'}"></div>
    <div class="bar" :style="{'--bar-height': bar13height + '%'}"></div>
    <div class="bar" :style="{'--bar-height': bar14height + '%'}"></div>
    <div class="bar" :style="{'--bar-height': bar15height + '%'}"></div> 
    <div class="bar" :style="{'--bar-height': bar16height + '%'}"></div> 
    <div class="bar" :style="{'--bar-height': bar17height + '%'}"></div>  
    <div class="bar" :style="{'--bar-height': bar18height + '%'}"></div>  
    <div class="bar" :style="{'--bar-height': bar19height + '%'}"></div>  
    <div class="bar" :style="{'--bar-height': bar20height + '%'}"></div>

  </div>
  <div class="containerbutton">
    <Icon name="mdi:color" class="icon" size="3vw"/>
  </div>
  <div class="containerthemes">
    <ul class="themelist">
      <li class="green">Green</li>
      <li class="orange">Orange</li>
      <li class="blue">Blue</li>
      <li class="yellow">Yellow</li>
      <li class="pink">Pink</li>
    </ul>
</div>
</template>

<script lang="js" setup>
import { onMounted } from 'vue';


const bar1height = ref(0);
const bar2height = ref(0);
const bar3height = ref(0);
const bar4height = ref(0);
const bar5height = ref(0);
const bar6height = ref(0);
const bar7height = ref(0);
const bar8height = ref(0);
const bar9height = ref(0);
const bar10height = ref(0);
const bar11height = ref(0);
const bar12height = ref(0);
const bar13height = ref(0);
const bar14height = ref(0);
const bar15height = ref(0);
const bar16height = ref(0);
const bar17height = ref(0);
const bar18height = ref(0);
const bar19height = ref(0);
const bar20height = ref(0);

const backgroundColor = ref('#1f1d2e');
const barColor = ref('#f6c177');
const backBarColor = ref('#191724');


onMounted(() => {
  let barheights = [bar1height, bar2height, bar3height, bar4height, bar5height, bar6height, bar7height, bar8height, bar9height, bar10height, bar11height, bar12height, bar13height, bar14height, bar15height, bar16height, bar17height, bar18height, bar19height, bar20height]

  navigator.mediaDevices
    .getUserMedia({ audio: true })
    .then((MediaStream) => {
      const audioCtx = new AudioContext();
      const source = audioCtx.createMediaStreamSource(MediaStream);
      const analyser = audioCtx.createAnalyser();
      source.connect(analyser);
      const bufferLength = 20;
      const dataArray = new Uint8Array(bufferLength);
    
      getAudio()
      setInterval(() => {
        barheights.forEach((bar, index) => {
          const currentHeight = bar.value
          const targetHeight = (dataArray[index]-122) / 6 * 100
          console.log((dataArray[index]-122) / 6 * 100)
          const transitionSpeed = 0.01
          const interpolatedHeight = currentHeight + (targetHeight - currentHeight) * transitionSpeed;
          bar.value = interpolatedHeight
        })
      }, 0.1)
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
    #f6c177 var(--bar-height),
    #f6c177
  );
  height: 80vh;
  width: 3vw;
  border-radius: 5px;
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
  margin: 0px;
  padding-left: 0px;
}
li {
  padding: 10px;
  cursor: pointer;
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