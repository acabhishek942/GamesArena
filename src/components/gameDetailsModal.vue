<template>
  <transition name="modal" v-if="isActive">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="modal-header">
            <slot name="header">
              <p>
                {{ game.title }}
                <span class="close" v-on:click="closeGameDetails()">
                  &times;
                </span>
              </p>
            </slot>
          </div>
          <div>
            <img src='http://ecx.images-amazon.com/images/I/21-leKb-zsL._SL500_AA300_.png' class='gamesImage'>
          </div>
          <h4>Genre : {{ game.genre }}</h4>
          <h4>Platform(s) : {{ game.platform }}</h4>
          <h4>Release Year : {{ game.release_year }}</h4>
          <h4>Score : {{ game.score }}</h4>
          <h4>Link : {{ game.url }}</h4>
          <div class="modal-footer">
            <slot name="footer">
              <p>
                That's All the details
              </p>
            </slot>
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
  margin: 0px auto;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
  transition: all .3s ease;
  font-family: Helvetica, Arial, sans-serif;
}

.modal-header p{
  margin-top: 0;
  color: lightgreen;
  font-size: 40px;
  text-align: center;
  width: 100%;

}

.modal-header {
  background-color: #222;
  height: 50px;
}

.modal-footer p{
  margin-top: 0;
  color: lightgreen;
  font-size: 40px;
  text-align: center;
  width: 100%;

}

.modal-footer {
  background-color: #222;
  height: 50px;
  text-align: center;
}

.modal-body {
  margin: 20px 0;
}

.modal-body p {
  padding-left: 200px;
}

.modal-default-button {
  float: right;
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

/* The Close Button */
.close {
    color: white;
    float: right;
    font-size: 28px;
    font-weight: bold;
    padding-right: 10px;
}

.close:hover,
.close:focus {
    color: lightgreen;
    text-decoration: none;
    cursor: pointer;
}

.gamesImage {
margin-left: 20px;
margin-top: 20px;
margin-bottom: 20px;
float: left;
height: 170px;
width: 200px;
}

h4 {
  margin: 20px;
}

</style>
