<template>
  <div v-if="!isListVisiable">
    <h2 class="text-slate-800 mb-3 font-bold text-2xl">Vue Music Player</h2>
    <div
      v-for="(song, songIndex) in list"
      :key="song.id"
      class="flex flex-row justify-between mb-1 cursor-pointer text-left p-3 mr-3 ml-3 bg-opacity-30 bg-white bg-clip-padding rounded-xl"
      @click="changeSong(songIndex)"
    >
      <div>
        <span class="text-slate-700 font-bold text-m m-0 p-0">{{
          song.name
        }}</span>
        <br />
        <span class="text-slate-500 text-xs"
          >{{ song.artistName }} - {{ song.albumName }} ({{ song.year }})</span
        >
      </div>
      <div>
        <img :src="song.src" alt="" class="max-h-12 rounded-lg shadow-xl" />
      </div>
    </div>
  </div>
  <SongPlayer
    v-if="isListVisiable"
    v-bind:song="list[currentSongIndex]"
    @goback="goback"
    @next="playNext"
    @previous="playPrevious"
  />
</template>

<script>
import SongPlayer from "./SongPlayer.vue";
export default {
  name: "SongList",
  components: { SongPlayer },
  methods: {
    changeSong(songindex) {
      this.currentSongIndex = songindex;
      this.isListVisiable = true;
    },
    goback() {
      this.isListVisiable = false;
    },
    playNext() {
      if (this.currentSongIndex < this.list.length - 1) {
        this.currentSongIndex += 1;
      } else {
        this.currentSongIndex = 0;
      }
    },
    playPrevious() {
      if (this.currentSongIndex != 0) {
        this.currentSongIndex -= 1;
      } else {
        this.currentSongIndex = this.list.length - 1;
      }
    },
  },
  data() {
    return {
      isListVisiable: false,
      currentSongIndex: 0,
      list: [
        {
          id: 1,
          name: "Cheap Thrills",
          artistName: "Adam Lambert",
          albumName: "Everything",
          year: 2021,
          src: `https://source.unsplash.com/random/400x400?date=1`,
          songSrc: `https://www.mboxdrive.com/ek.mp3`,
        },
        {
          id: 2,
          name: "Lean on",
          artistName: "Adam Levine",
          albumName: "Goind Down",
          year: 2001,
          src: `https://source.unsplash.com/random/400x400?date=2`,
          songSrc: `https://www.mboxdrive.com/1.mp3`,
        },
        {
          id: 3,
          name: "Counting Stars",
          artistName: "Adam Hart",
          albumName: "Spice It Up",
          year: 2013,
          src: `https://source.unsplash.com/random/400x400?date=3`,
          songSrc: `https://www.mboxdrive.com/8.mp3`,
        },
        {
          id: 4,
          name: "Cheap Thrills",
          artistName: "Adam Lambert",
          albumName: "Everything",
          year: 2021,
          src: `https://source.unsplash.com/random/400x400?date=4`,
          songSrc: `https://www.mboxdrive.com/10.mp3`,
        },
        {
          id: 5,
          name: "Lean on",
          artistName: "Adam Levine",
          albumName: "Goind Down",
          year: 2001,
          src: `https://source.unsplash.com/random/400x400?date=5`,
          songSrc: `https://www.mboxdrive.com/mkk.mp3`,
        },
        {
          id: 6,
          name: "Counting Stars",
          artistName: "Adam Hart",
          albumName: "Spice It Up",
          year: 2013,
          src: `https://source.unsplash.com/random/400x400?date=6`,
          songSrc: `https://www.mboxdrive.com/putra.mp3`,
        },
      ],
    };
  },
};
</script>

<style scoped></style>
