<script setup>
import SongItem from './components/Song.vue';
import { ref, computed } from 'vue';
import artists from "@/artists" ;
import songs from "@/songs";
let filteredSongs = ref([]);
let SelectedArtist = ref(undefined);

window.onload = (event) => {
  ChangedArtist(event);
};

function SelectAll(){
  SelectedArtist.value = artist;
  filteredSongs.value = songs;
}
function FilterSongs(event){
  SelectedArtist.value = artists.find((e)=> e._id == event.target.value);
  filteredSongs.value = songs.filter(x=>x.ARTIST_ID == SelectedArtist.value._id)
  
}

function ChangedArtist(event){
  if(SelectedArtist.value == undefined || event.target[0].selected){
    SelectAll();
  }
  else{
    FilterSongs(event);
   }
}


</script>

<template>
  <h1 class="mb-5">Songs & Artists</h1>
  <div class="justify-content-start">
    <div class="mb-1">
      <select class="form-select" v-on:change="ChangedArtist($event)" name="artist" id="artist">
        <option selected>Select an Artist</option>
        <option v-for="(artist, index) in artists" :value="artist._id" :songs="songs">{{ artist.artist }}</option>
      </select>
    </div>
  </div>
  
  <div class="justify-content-center m-5">
    <table class="table">
      <thead>
        <tr>
          <th scope="col">Title</th>
          <th scope="col">Year</th>
          <th scope="col">Time</th>
          <th scope="col">BPM</th>
          <th scope="col">Genre</th>
        </tr>
      </thead>
      <tbody>
        <SongItem v-for="(song, index) in filteredSongs" :song="song"/>
      </tbody>
    </table>
  </div>

</template>

<style>

</style>
