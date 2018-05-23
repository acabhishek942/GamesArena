<template>
  <transition name="modal" v-if="isActive">
    <div class="modal-mask">
      <div class="modal-wrapper">
        <div class="modal-container">
          <div class="modal-header">
            <slot name="header">
              <p>
                {{ game.title }}
              </p>
            </slot>
          </div>
          <div class="modal-body">
            <slot name="body">
              Genre : {{ game.genre }}
            </slot>
          </div>
          <div class="modal-body">
            <slot name="body">
              Platform(s) : {{ game.platform }}
            </slot>
          </div>
          <div class="modal-body">
            <slot name="body">
              Release Year : {{ game.release_year }}
            </slot>
          </div>
          <div class="modal-body">
            <slot name="body">
              Score : {{ game.score }}
            </slot>
          </div>
          <div class="modal-body">
            <slot name="body">
              Link : {{ game.url }}
            </slot>
          </div>
          <div class="modal-footer">
            <slot name="footer">
              That's All the details
              <button class="modal-default-button" v-on:click="closeGameDetails()">
              OK
              </button>
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
  width: 70%;
  margin: 0px auto;
  padding: 20px 30px;
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

}

.modal-header {
  background-color: #222;
  height: 50px;
}

.modal-body {
  margin: 20px 0;
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

</style>
