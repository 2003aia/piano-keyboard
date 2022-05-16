<template>
  <div
    v-bind:class="{
      buttonOn: startPiano === true,
      button: startPiano === false,
    }"
  ></div>
</template>

<script>
export default {
  name: "button",
  props: {
    startPiano: {
      type: Boolean,
      required: true,
    },
  },
};
</script>


<style scoped>
.buttonOn {
  background: rgb(255, 238, 0);
  height: 20px;
  width: 6px;
  border-radius: 1px;
  margin: auto;
  border: rgb(0, 0, 0) solid 1px;
}
.button {
  height: 20px;
  width: 6px;
  background: #eee;
  border-radius: 1px;
  margin: auto;
  border: rgb(0, 0, 0) solid 1px;
}
</style>