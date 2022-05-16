<template>
  <div
    v-bind:class="{
      pianoKeys: note.white != octaveNotes.white,
      pianoKeysActive: note.white === octaveNotes.white,
    }"
  >
    <div v-on:click="$emit('play', note.white[0])" class="white">
      <span>
        {{ note.white[0] }}
      </span>
    </div>

    <div v-on:click="$emit('play', note.black[0])" class="black">
      <span>
        {{ note.black[0] }}
      </span>
    </div>

    <div v-on:click="$emit('play', note.white[1])" class="white">
      <span>
        {{ note.white[1] }}
      </span>
    </div>
    <div v-on:click="$emit('play', note.black[1])" class="black">
      <span>
        {{ note.black[1] }}
      </span>
    </div>
    <div v-on:click="$emit('play', note.white[2])" class="white">
      <span>
        {{ note.white[2] }}
      </span>
    </div>
    <div v-on:click="$emit('play', note.white[3])" class="white">
      <span>
        {{ note.white[3] }}
      </span>
    </div>
    <div v-on:click="$emit('play', note.black[2])" class="black">
      <span>
        {{ note.black[2] }}
      </span>
    </div>
    <div v-on:click="$emit('play', note.white[4])" class="white">
      <span>
        {{ note.white[4] }}
      </span>
    </div>
    <div v-on:click="$emit('play', note.black[3])" class="black">
      <span>
        {{ note.black[3] }}
      </span>
    </div>
    <div v-on:click="$emit('play', note.white[5])" class="white">
      <span>
        {{ note.white[5] }}
      </span>
    </div>
    <div v-on:click="$emit('play', note.black[4])" class="black">
      <span>
        {{ note.black[4] }}
      </span>
    </div>
    <div v-on:click="$emit('play', note.white[6])" class="white">
      <span>
        {{ note.white[6] }}
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: "keys",
  props: {
    octaveNotes: {
      type: Object,
      required: false,
    },
    note: {
      type: Object,
      required: true,
    },
  },
  methods: {
    c: function () {
      console.log(
        this.octaveNotes.white,
        this.note.white,
        "notes",
        this.note.white === this.octaveNotes.white
      );
    },
  },
};
</script>


<style scoped>
.pianoKeys {
  display: flex;
  justify-content: center;
}

.pianoKeysActive {
  border-bottom: solid 4px rgb(4, 164, 237);
  display: flex;
  justify-content: center;
}
.black {
  box-shadow: 5px 5px 5px rgb(175, 175, 175);

  transition: 1s;
  height: 200px;
  width: 25px;
  margin-left: -14px;
  margin-right: -13px;
  z-index: 1000;
  background: #000;
  border: #000 solid 1px;
  color: #fff;
  position: relative;
  font-size: 14px;
  overflow: hidden;
}

span {
  position: absolute;
  left: 0;
  bottom: 0;
}

.white {
  box-shadow: 2px 2px 10px rgb(49, 49, 49);

  height: 300px;
  width: 50px;
  background: #fff;
  border: #000 solid 1px;
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;
  position: relative;
}

.white:active {
  background-image: linear-gradient(
    0deg,
    #d0d322 0%,
    #e7e38e 23%,
    #ffffff 100%
  );
}

.black:active {
  background-image: linear-gradient(
    0deg,
    #d0d322 0%,
    #343323 23%,
    #000000 100%
  );
}
</style>