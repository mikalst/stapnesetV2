<template>
  <transition name="fade" v-if="pageloaded">
    <div class="base" v-bind:class="{top: top, left: left, highlight: hover }">
    <a class="nonhighlight" v-on:mouseover="hover=true" v-on:mouseleave="hover=false">
      {{ msg }}
      </a>
  </div>
  </transition>
</template>

<script>
export default {
  name: 'Hyperlink',
  props: {
    msg: String,
    top: Boolean,
    left: Boolean,
    color: {
      default: 'azure',
      type: String
    },
  },
  computed: {
  },
  data() {
    return {
      pageloaded: false,
      hover: false
    };
  },
  created() {
    setTimeout(() => { this.pageloaded = true; }, 300);
  }
}
</script>

<style scoped>
.base{
  position: absolute;
  top: 75%;
  left: 55%;
  width: 40%;
  z-index: 1;
  word-wrap: normal;
  text-align: right;
  color: azure;
}
.top{
  top: 25%;
  color: darkslategray;
}
.left{
  left: 5%;
  text-align: left;
}

@media screen and (max-width: 600px) {
  .base{
    font-size: 7vw;
  }
}
@media screen and (min-width: 601px) {
  .base{
    font-size: 42px;
  }
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 1.0s ease-in-out;
}
.fade-enter, .fade-leave-active {
  opacity: 0;
}
.highlight{
  opacity: 0.5;
  transition: opacity 0.5s ease-in;
}
</style>



