<template>
  <div class="btn-grp">
    <button class="btn1" v-on:click="count = 10 ,seconds='00'">Pomodoro</button>
    <button class="btn2" v-on:click="count = 5, seconds='00'">Short Break</button>
    <button class="btn3" v-on:click="count = 15,seconds='00'">Long Break</button>
    <!--<button class="startBtn" v-on:click="startPomo">Start</button>-->
    <h1 class="count">{{ count }} : {{seconds}}</h1>
    <button class="newStartBtn" v-on:click="startPomo">Start</button>
  </div>
</template>

<script>
export default {
  name: "MyComponent",
  data: function() {
    return {
      count: 0,
      seconds:0
    };
  },
  methods: {
    greet: function(event) {
      // `this` inside methods points to the Vue instance

      if (event) {
        localStorage.setItem("color", "Red");
        alert("Hello World!");
      }
    },

    startPomo: function(event) {
      if (event) {
        console.log('start button clicked!');
        var timerCount = 0;
        var timerId = setInterval(()=>{

          timerCount=60000;
          this.seconds = 60;
          var secondTimer = setInterval(()=>{
            if(this.seconds==1){
              clearInterval(secondTimer);
            }
            this.seconds--;
            console.log('seconds are '+this.seconds);
          },1000);
          if(this.count==1){
            clearInterval(timerId);
          }
          this.count--;
        },timerCount);
        
      }
    },
  },
};
</script>

<style scoped>

button{
  width:75px;
  height: 50px;
}

.btn-grp {
  background-color: #ec7470;
}

.btn1 {
  margin: 10px;
}

.btn2 {
  margin: 10px;
}

.btn3 {
  margin: 10px;
}

.newStartBtn{
  font-size: 30px;
  width: 150px;
  height: 50px;
  color: #d44d48;
  border: none;
  border-radius: 5%;
}
.count{
  margin: 10px;
  font-size: 50px;
}
</style>
