<template>
  <audio :src="song.songSrc" preload="auto" autoplay ref="audioPlayer"></audio>
  <div class="text-white">
    <div class="flex flex-row justify-between p-2 mb-2">
      <button
        @click="goback"
        class="text-white text-sm bg-amber-600 pt-1 pb-1 pl-4 pr-4 rounded-full"
      >
        Back
      </button>
      <div class="text-slate-700 font-bold text-1xl">VueJs Music App</div>
    </div>
    <div>
      <img :src="song.src" alt="" class="rounded-2xl shadow-2xl" />
    </div>
    <div class="flex flex-row justify-between icons-play m-auto mt-5">
      <i
        class="fa-solid fa-angles-left cursor-pointer text-slate-500"
        @click="previous"
      ></i>
      <i
        class="fa-solid fa-play text-slate-900 p-0 m-0 cursor-pointer"
        @click="togglePlay"
        v-if="!isPlaying"
      ></i>
      <i
        class="fa-solid fa-pause text-slate-900 p-0 m-0 cursor-pointer"
        @click="togglePlay"
        v-if="isPlaying"
      ></i>
      <i
        class="fa-solid fa-angles-right cursor-pointer text-slate-500"
        @click="next"
      ></i>
    </div>
    <h2 class="text-slate-900 font-bold mt-4 text-m">{{ song.name }}</h2>
  </div>
</template>

<script>
export default {
  name: "SongPalyer",
  props: {
    song: {
      id: Number,
      name: String,
      artistName: String,
      albumName: String,
      year: Number,
      src: String,
      songSrc: String,
    },
  },
  data() {
    return {
      isPlaying: true,
    };
  },
  methods: {
    togglePlay() {
      if (this.isPlaying) {
        this.$refs.audioPlayer.pause();
      } else {
        this.$refs.audioPlayer.play();
      }
      this.isPlaying = !this.isPlaying;
    },
    goback() {
      this.$emit("goback");
    },
    next() {
      this.$emit("next");
    },
    previous() {
      this.$emit("previous");
    },
  },
  emits: ["goback", "next", "previous"],
};
</script>

<style scoped>
.icons-play {
  width: 200px;
}
</style>
