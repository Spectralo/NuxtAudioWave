<template>
  <div class="container">
    <div class="bar1">
    </div>
    <div class="bar2">
    </div>
    <div class="bar3">
    </div>
    <div class="bar4">
    </div>
    <div class="bar5">
    </div>
    <div class="bar6">
    </div>
    <div class="bar7">
    </div>
    <div class="bar8">
    </div>
    <div class="bar9">
    </div>
    <div class="bar10">
    </div>
  </div>
</template>

<script lang="js" setup>
import { onMounted } from 'vue';

let bar1height = 0;
let bar2height = 0;
let bar3height = 0;
let bar4height = 0;
let bar5height = 0;
let bar6height = 0;
let bar7height = 0;
let bar8height = 0;
let bar9height = 0;
let bar10height = 0;


onMounted(() => {
  navigator.mediaDevices
    .getUserMedia({ audio: true })
    .then((MediaStream) =>
      setInterval(() => {
        console.log(MediaStream.getAudioTracks())
      }, 1000)
    )
});


</script>



<style>
body {
  background-color: #1f1d2e;
}
.bar {
  background: linear-gradient(
    to top, 
    #f6c177,
    #f6c177 50%,
    #191724 50%,
    #191724
  );
  height: 80vh;
  width: 3vw;
  border-radius: 5px;
}

.bar1 {
  background: linear-gradient(
    to top, 
    #f6c177,
    #f6c177 50%,
    #191724 50%,
    #191724
  );
  height: 80vh;
  width: 3vw;
  border-radius: 5px;
}

.bar2 {
  background: linear-gradient(
    to top, 
    #f6c177,
    #f6c177 50%,
    #191724 50%,
    #191724
  );
  height: 80vh;
  width: 3vw;
  border-radius: 5px;
}

.bar3 {
  background: linear-gradient(
    to top, 
    #f6c177,
    #f6c177 50%,
    #191724 50%,
    #191724
  );
  height: 80vh;
  width: 3vw;
  border-radius: 5px;
}

.bar4 {
  background: linear-gradient(
    to top, 
    #f6c177,
    #f6c177 50%,
    #191724 50%,
    #191724
  );
  height: 80vh;
  width: 3vw;
  border-radius: 5px;
}

.bar5 {
  background: linear-gradient(
    to top, 
    #f6c177,
    #f6c177 50%,
    #191724 50%,
    #191724
  );
  height: 80vh;
  width: 3vw;
  border-radius: 5px;
}

.bar6 {
  background: linear-gradient(
    to top, 
    #f6c177,
    #f6c177 50%,
    #191724 50%,
    #191724
  );
  height: 80vh;
  width: 3vw;
  border-radius: 5px;
}

.bar7 {
  background: linear-gradient(
    to top, 
    #f6c177,
    #f6c177 50%,
    #191724 50%,
    #191724
  );
  height: 80vh;
  width: 3vw;
  border-radius: 5px;
}

.bar8 {
  background: linear-gradient(
    to top, 
    #f6c177,
    #f6c177 50%,
    #191724 50%,
    #191724
  );
  height: 80vh;
  width: 3vw;
  border-radius: 5px;
}

.bar9 {
  background: linear-gradient(
    to top, 
    #f6c177,
    #f6c177 50%,
    #191724 50%,
    #191724
  );
  height: 80vh;
  width: 3vw;
  border-radius: 5px;
}

.bar10 {
  background: linear-gradient(
    to top, 
    #f6c177,
    #f6c177 50%,
    #191724 50%,
    #191724
  );
  height: 80vh;
  width: 3vw;
  border-radius: 5px;
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