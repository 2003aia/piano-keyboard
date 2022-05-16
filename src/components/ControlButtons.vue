<template>
  <div class="control">
    <div class="button-wrapper" v-on:click="$emit('start')">
    <span class="comments">Кнопка включения</span>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="20"
        height="20"
        fill="silver"
        class="bi bi-lightbulb-fill"
        viewBox="0 0 16 16"
      >
        <path
          d="M2 6a6 6 0 1 1 10.174 4.31c-.203.196-.359.4-.453.619l-.762 1.769A.5.5 0 0 1 10.5 13h-5a.5.5 0 0 1-.46-.302l-.761-1.77a1.964 1.964 0 0 0-.453-.618A5.984 5.984 0 0 1 2 6zm3 8.5a.5.5 0 0 1 .5-.5h5a.5.5 0 0 1 0 1l-.224.447a1 1 0 0 1-.894.553H6.618a1 1 0 0 1-.894-.553L5.5 15a.5.5 0 0 1-.5-.5z"
        />
      </svg>
      <Button :startPiano="startPiano" />
    </div>
    <div class="button-wrappers">
      <span class="comments">Громкость</span>
      <div class="button-wrapper2">
        <div class="button-icons-top">
          <div class="circle" v-bind:class="{ circleActive: volume === -5 }" />
          <div class="circle" v-bind:class="{ circleActive: volume === 0 }" />
          <div class="circle" v-bind:class="{ circleActive: volume === 5 }" />
          <div class="circle" v-bind:class="{ circleActive: volume === 10 }" />
          <div class="circle" v-bind:class="{ circleActive: volume === 15 }" />
        </div>
        <span class="text"> Volume </span>

        <Button v-on:click="$emit('volumeDecrement')" />
        <Button v-on:click="$emit('volumeIncrement')" />
      </div>
    </div>
    <div class="button-wrappers">
      <span class="comments">Октавы</span>
      <div class="button-wrapper2">
        <Button v-on:click="$emit('octaveDecrement')" />
        <Button v-on:click="$emit('octaveIncrement')" />
        <div class="button-icons-bottom">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="16"
            height="16"
            fill="silver"
            class="bi bi-caret-left-fill"
            viewBox="0 0 16 16"
          >
            <path
              d="m3.86 8.753 5.482 4.796c.646.566 1.658.106 1.658-.753V3.204a1 1 0 0 0-1.659-.753l-5.48 4.796a1 1 0 0 0 0 1.506z"
            />
          </svg>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="16"
            height="16"
            fill="silver"
            class="bi bi-caret-right-fill"
            viewBox="0 0 16 16"
          >
            <path
              d="m12.14 8.753-5.482 4.796c-.646.566-1.658.106-1.658-.753V3.204a1 1 0 0 1 1.659-.753l5.48 4.796a1 1 0 0 1 0 1.506z"
            />
          </svg>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Button from "./Button.vue";
export default {
  name: "controlButtons",
  components: { Button },
  props: {
    startPiano: {
      type: Boolean,
      required: true,
    },
    volume: Number,
  },
};
</script>


<style scoped>
.comments{
  position:absolute;
  color: grey;
  top: -30px;
  right: 5px;
}
.circle {
  width: 5px;
  height: 5px;
  border-radius: 50%;
  background: silver;
}

.circleActive {
  width: 5px;
  height: 5px;
  border-radius: 50%;
  background: yellow;
}
.text {
  color: #fff;
  font-size: 10px;
  position: absolute;
  top: 20px;
}
.control {
  padding: 10px;
  display: flex;
}
.button-icons-top {
  display: flex;
  /* height: 60px; */
  width: 42px;
  left: 10px;
  position: absolute;
  top: 5px;
  justify-content: space-between;
}
.button-icons-bottom {
  display: flex;
  height: fit-content;
  width: 30px;
  position: absolute;
  bottom: -5px;
  justify-content: space-between;
}
.button-wrapper2 {
  display: flex;
  height: fit-content;
  width: 30px;
  padding: 10px;
  height: 50px;
  margin-top: 21px;
  border-radius: 50%;
  justify-content: space-between;
}

.button-wrapper2:active {
  background: rgb(255, 255, 255, 0.2);
}

.button-wrapper {
  border-radius: 50%;
  position: relative;
  width: fit-content;
  padding: 10px;
}
.button-wrappers {
  position: relative;
  height: 55px;
  width: fit-content;
  padding: 5px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.button-wrapper:active {
  background: rgb(255, 255, 255, 0.2);
}
</style>