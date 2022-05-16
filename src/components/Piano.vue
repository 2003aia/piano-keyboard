<template>
  <div class="main">
    <div class="piano">
      <ControlButtons
        v-on:octaveIncrement="octaveIncrement"
        v-on:octaveDecrement="octaveDecrement"
        :startPiano="startPiano"
        v-on:start="start"
        :volume="volume"
        v-on:volumeIncrement="volumeIncrement"
        v-on:volumeDecrement="volumeDecrement"
      />
      <div class="wrapper">
        <Keys
          v-for="note of notes"
          v-bind:note="note"
          v-on:play="play"
          :octaveNotes="octaveNotes"
          v-bind:key="note"
        />
      </div>
    </div>
  </div>
</template>

<script>
import * as Tone from "tone";
import Keys from "./Keys.vue";
import Button from "./Button.vue";
import ControlButtons from "./ControlButtons.vue";

const notes = [
  {
    white: ["C2", "D2", "E2", "F2", "G2", "A2", "B2"],
    black: ["C#2", "D#2", "F#2", "G#2", "A#2", "A#2", "B#2"],
  },
  {
    white: ["C3", "D3", "E3", "F3", "G3", "A3", "B3"],
    black: ["C#3", "D#3", "F#3", "G#3", "A#3", "A#3", "B#3"],
  },
];

export default {
  data() {
    return {
      octaveNotes: {},
      startPiano: false,
      notes: notes,
      octave: 0,
      volume: 0,
    };
  },

  components: {
    Keys,
    Button,

    ControlButtons,
  },
  mounted() {
    const keys = (event) => {
      const synth = new Tone.Synth().toDestination();
      synth.volume.value = this.volume;
      console.log(this.volume, "volume");
      notes.filter((d, index) => {
        if (this.startPiano) {
          if (event.keyCode === 90) {
            if (this.octave > 0) {
              this.octave -= 1;
            }
          }
          if (event.keyCode === 88) {
            if (this.octave < 1) {
              this.octave += 1;
            }
          }

          if (index === this.octave) {
            Object.assign(this.octaveNotes, d);

            if (event.keyCode === 87) {
              synth.triggerAttackRelease(d.black[0], "8n");
            }
            if (event.keyCode === 69) {
              synth.triggerAttackRelease(d.black[1], "8n");
            }
            if (event.keyCode === 82) {
              synth.triggerAttackRelease(d.black[2], "8n");
            }
            if (event.keyCode === 84) {
              synth.triggerAttackRelease(d.black[3], "8n");
            }
            if (event.keyCode === 89) {
              synth.triggerAttackRelease(d.black[4], "8n");
            }

            if (event.keyCode === 65) {
              synth.triggerAttackRelease(d.white[0], "8n");
            }
            if (event.keyCode === 83) {
              synth.triggerAttackRelease(d.white[1], "8n");
            }
            if (event.keyCode === 68) {
              synth.triggerAttackRelease(d.white[2], "8n");
            }
            if (event.keyCode === 70) {
              synth.triggerAttackRelease(d.white[3], "8n");
            }
            if (event.keyCode === 71) {
              synth.triggerAttackRelease(d.white[4], "8n");
            }
            if (event.keyCode === 72) {
              synth.triggerAttackRelease(d.white[5], "8n");
            }
            if (event.keyCode === 74) {
              synth.triggerAttackRelease(d.white[6], "8n");
            }
          }
        }
      });
    };
    window.addEventListener("keydown", keys);
  },

  methods: {
    play: function (note) {
      if (this.startPiano === true) {
        const synth = new Tone.Synth().toDestination();
        synth.volume.value = this.volume;
        synth.triggerAttackRelease(note, "8n");
      }
    },

    start: function () {
      let self = this;
      self.startPiano = !self.startPiano;
      const toneStart = async () => {
        await Tone.start();
        console.log("started piano", this.startPiano);
      };
      toneStart();
    },
    octaveIncrement: function () {
      if (this.startPiano) {
        synth.volume.value = this.volume;
        if (this.octave < 1) {
          this.octave += 1;
        }
      }
    },
    octaveDecrement: function () {
      if (this.startPiano) {
        if (this.octave > 0) {
          this.octave -= 1;
        }
      }
    },
    volumeDecrement: function () {
      const synth = new Tone.Synth().toDestination();
      synth.volume.value = this.volume;
      if (this.volume > -10) {
        this.volume -= 5;
      }
    },
    volumeIncrement: function () {
      const synth = new Tone.Synth().toDestination();
      synth.volume.value = this.volume;
      if (this.volume < 15) {
        this.volume += 5;
      }
    },
  },
};
</script>

<style scoped>
.wrapper {
  display: flex;
  border: solid 4px #000;
  position: relative;
  height: 330px;
  border-bottom: 1px solid #000;
  background: rgb(79, 79, 79);
}

.piano {
  border-radius: 20px;
  background: rgb(79, 79, 79);
  padding: 20px;
  padding-top: 40px;
  display: block;
  padding-bottom: 0;
  width: fit-content;
  margin: auto;
}
</style>