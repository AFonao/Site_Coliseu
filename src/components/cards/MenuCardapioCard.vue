<template>
  <div class="Card2 ph1" :style="style">
    <div class="overlay">
      <slot name="title"></slot>
      <slot name="botao"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "menu-card",
  props: {
    headerColor: {
      type: String,
      default: "",
    },
    url: {
      type: String,
      default: "",
    },
  },
  data() {
    return {
      cardHidden: true,
    };
  },
  beforeMount() {
    setTimeout(this.showCard, 400);
  },
  methods: {
    showCard: function () {
      this.cardHidden = false;
    },
    getClass: function (headerColor) {
      return "md-card-header-" + headerColor + " card-my-card-color";
    },
  },
  computed: {
    style() {
      return (
        "background: url(" +
        this.url +
        ") center no-repeat;background-size: cover;"
      );
    },
  },
};
</script>

<style lang="css" scoped>
* {
  margin: 0px;
  padding: 0px;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  font-family: "Roboto";
}

.Card2 {
  position: relative;
  display: inline-block;
  width: 300px;
  height: 300px;
  margin: 1em;
  background-size: cover;
  border-radius: 10px;
  box-shadow: 0px 25px 50px rgba(0, 0, 0, 0.5);
  overflow: hidden;
  -moz-transition: 0.5s;
  -o-transition: 0.5s;
  -webkit-transition: 0.5s;
  transition: 0.5s;
}

.Card2 .overlay {
  width: 100%;
  height: 100%;
  position: absolute;
  padding: 1em;
  top: 0;
  z-index: 10;
  color: #fff;
  -moz-transition: 0.5s;
  -o-transition: 0.5s;
  -webkit-transition: 0.5s;
  transition: 0.5s;
}

.Card2 .overlay h2 {
  position: relative;
  margin: 2em 0px;
  top: -200px;
  -moz-transition: 0.5s;
  -o-transition: 0.5s;
  -webkit-transition: 0.5s;
  transition: 0.5s;
}

.Card2 .overlay a {
  position: relative;
  width: 60%;
  top: 200px;
  padding: 0.5em 2em;
  border: 2px solid #fff;
  text-decoration: none;
  color: #ffffff;
  border-radius: 3px;
  -moz-transition: 0.5s;
  -o-transition: 0.5s;
  -webkit-transition: 0.5s;
  transition: 0.5s;
}
.Card2 a:hover {
  background: #fff;
  color: #5c5c5c;
}

.Card2:hover .overlay {
  background: rgba(92, 92, 92, 0.8);
}
.Card2:hover h2 {
  top: 0px;
}
.Card2:hover a {
  top: 0px;
}

@media screen and (max-width: 700px) {
  /* --- Card2 ---- */

  .Card2 {
    position: relative;
    display: block;
    width: 100%;
    height: 300px;
    margin: 3em 0em;
    border-radius: 0px;
    box-shadow: 0px 25px 50px rgba(0, 0, 0, 0.5);
    overflow: hidden;
    transition: all 0.4s ease;
  }
}
</style>
