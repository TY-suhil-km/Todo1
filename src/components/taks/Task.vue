<template>
  <div id="container">
    <div>
      
      <button @mousedown="handelMousedown" @mouseup="myStopFunction">
        Click
      </button>
      <h1>{{ this.count }}</h1>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";

@Component
export default class Task extends Vue {
  count = 0;
  timeDelay = 500;
  myInterval: any;

  public handelclick(): void {
    this.count = this.count + 1;
  }

  public handelMousedown(): any {
    this.count += 1;
    setTimeout(this.mouseDownCount, this.timeDelay * 5);
  }

  public mouseDownCount(): any {
    this.myInterval = setInterval(
      () => (this.count = this.count + 1),
      this.timeDelay
    );
  }

  public myStopFunction() {
    clearInterval(this.myInterval);
    setTimeout(() => {
      clearInterval(this.myInterval);
    }, this.timeDelay * 5);
  }
}
</script>
<style scoped>
#container div {
  margin: auto;
  width: 50%;
}
button {
  width: 100px;
  height: 40px;
  
}
</style>