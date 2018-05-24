<template>
  <transition name="modal" v-if="isActive">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="modal-header">
            <slot name="header">
              <p>
                <b><i>{{ game.title }}</i></b>
                <span class="close" v-on:click="closeGameDetails()">
                &times;
                </span>
              </p>
            </slot>
          </div>
          <div class='gamesImage'>
            <img src='https://www.callofduty.com/content/dam/atvi/callofduty/wwii/home/Stronghold_Metadata_Image.jpg' />
            <h4>Genre : {{ game.genre }}<br /><br />
              Platform(s) : {{ game.platform }}<br /><br />
              Release Year : {{ game.release_year }}<br /><br />
              Score : {{ game.score }}<br /><br />
              Link : {{ game.url }}
            </h4>
            <br /><br />
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
import { bus } from '../main';
export default {
  data () {
    return {
      isActive: false,
      game: {}
    }
  },
  methods:{
    closeGameDetails: function () {
      this.isActive = false;
    }
  },
  created(){
    bus.$on('show-game-detail-modal', (data) => {
      this.game.title = data.title;
      this.game.editors_choice = data.editors_choice;
      this.game.genre = data.genre;
      this.game.platform = data.platform;
      this.game.release_year = data.release_year;
      this.game.score = data.score;
      this.game.url = data.url;
      this.isActive = true;
    })
  }
}
</script>

<style scoped>

h4 {
  margin: 40px;
  position: absolute;
  color: white;
  top: 150px;
}
/* The Close Button */
.close {
  color: #7f8793;
  float: right;
  font-size: 28px;
  font-weight: bold;
  padding-right: 10px;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}

.gamesImage {
  margin-left: 20px;
  margin-bottom: 20px;
  float: left;
  height: 170px;
  width: 95%;
  position: relative;
}

.gamesImage img{
  margin-left: 20px;
  margin-top: 20px;
  margin-bottom: 20px;
  float: left;
  height: 350px;
  width: 95%;
  position: relative;
}

.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, .5);
  display: table;
  transition: opacity .3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 50%;
  height: 45%;
  margin: 0px auto;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
  transition: all .3s ease;
  font-family: Helvetica, Arial, sans-serif;
}

.modal-header p{
  margin-top: 0;
  font-size: 50px;
  text-align: center;
  width: 100%;
  color: #7f8793;
}

.modal-header {
  height: 50px;
}

/*
 * The following styles are auto-applied to elements with
 * transition="modal" when their visibility is toggled
 * by Vue.js.
 *
 * You can easily play with the modal transition by editing
 * these styles.
 */

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
</style>
