<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style lang="scss">
  @import '~normalize.css/normalize';
  @import "./assets/scss/_mixins.scss";
  #app {
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
    width: 100%;
    height: 100%;
}

  @font-face {
    font-family: 'Helvetica-Black';
    src: url('./assets/fonts/HelveticaNeueCyr-Black.eot');
    src: local('☺'), url('./assets/fonts/HelveticaNeueCyr-Black.woff') format('woff'), url('./assets/fonts/HelveticaNeueCyr-Black.ttf') format('truetype'), url('./assets/fonts/HelveticaNeueCyr-Black.svg') format('svg');
    font-weight: normal;
    font-style: normal;
  }

  @font-face {
    font-family: 'Helvetica-Bold';
    src: url('./assets/fonts/HELVETICANEUECYR-BOLD_0.eot');
    src: local('☺'),
    url('./assets/fonts/HELVETICANEUECYR-BOLD_0.ttf') format('truetype'),
    url('./assets/fonts/HELVETICANEUECYR-BOLD_0.svg') format('svg');
    font-weight: normal;
    font-style: normal;
  }

  @font-face {
    font-family: 'Helvetica-Light';
    src: url('./assets/fonts/HELVETICANEUECYR-LIGHT_0.eot');
    src: local('☺'),
    url('./assets/fonts/HELVETICANEUECYR-LIGHT_0.ttf') format('truetype'),
    url('./assets/fonts/HELVETICANEUECYR-LIGHT_0.svg') format('svg');
    font-weight: normal;
    font-style: normal;
  }

  @font-face {
    font-family: 'Helvetica-Medium';
    src: url('./assets/fonts/HELVETICANEUECYR-MEDIUM_0.eot');
    src: local('☺'), url('./assets/fonts/HELVETICANEUECYR-MEDIUM_0.ttf') format('truetype'), url('./assets/fonts/HELVETICANEUECYR-MEDIUM_0.svg') format('svg');
    font-weight: normal;
    font-style: normal;
  }

  @font-face {
    font-family: 'Helvetica-Roman';
    src: url('./assets/fonts/HELVETICANEUECYR-ROMAN_0.eot');
    src: local('☺'),
    url('./assets/fonts/HELVETICANEUECYR-ROMAN_0.ttf') format('truetype'),
    url('./assets/fonts/HELVETICANEUECYR-ROMAN_0.svg') format('svg');
    font-weight: normal;
    font-style: normal;
  }

  @font-face {
    font-family: 'Helvetica-Thin';
    src: url('./assets/fonts/HELVETICANEUECYR-THIN_0.eot');
    src: local('☺'),
    url('./assets/fonts/HELVETICANEUECYR-THIN_0.ttf') format('truetype'),
    url('./assets/fonts/HELVETICANEUECYR-THIN_0.svg') format('svg');
    font-weight: normal;
    font-style: normal;
  }

html, body {
  width: 100%;
  height: 100%;
  font-family: "Helvetica-Medium", Helvetica, sans-serif;
}

  * {
    box-sizing: border-box;
  }

  .fade-out-enter-active {
    transition: all 1s ease;
  }
  .fade-out-leave-active {
    display: none;
  }
  .fade-out-enter, .fade-out-leave-to {
    opacity: .5;
  }

  .opacity-in{
    opacity: 0;
  }

  .opacity-out{
    opacity: 1;
  }


  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
  }
  .fade-enter, .fade-leave-to /* .fade-leave-active до версии 2.1.8 */ {
    opacity: 0;
  }

  .test-item-wrapper {
    width: 100%;
    height: 100%;
    position: relative;
  }

  .test-number {
    font-family: 'Helvetica-Thin', sans-serif;
    font-size: 190px;
    color: #78cedd;
    @include desktop() {
      font-size: 124px;
    }
    @include phones() {
      font-size: 100px;
    }
  }

  .test-btn {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    border: 1px solid transparent;
    background-color: #78cedd;
    color: #fff;
    padding: 0 30px;
    width: 100%;
    height: 73px;
    border-radius: 50px;
    outline: none;
    cursor: pointer;
    transition: all .2s;
    @include desktop() {
      height: 55px;
    }
    @include laptop() {
      max-width: 360px;
      align-self: center;
      margin: auto;
    }
  }

  .test-btn:hover .arrow-right {
    transform: rotateZ(45deg) translate(4px, -4px);
    transition: all .2s;
  }



  .test-btn__text {
    font-family: "Helvetica-Roman", sans-serif;
    line-height: 33px;
    letter-spacing: 2px;
    font-size: 25px;
    margin-right: 10px;
    @include desktop() {
      font-size: 20px;
      margin-right: 5px;
    }
  }

  .arrow-right {
    display: inline-block;
    width: 17px;
    height: 17px;
    margin-right: 7px;
    border-top: 2px solid #fff;
    border-right: 2px solid #fff;
    transform: rotateZ(45deg) translate(0);
    transition: all .2s;
    @include desktop() {
      width: 12px;
      height: 12px;
    }
  }

  .test-btn.inverse {
    background-color: #fff;
    color: #78cedd;
    border: 3px solid #78cedd;
    transition: all .2s;
  }

  .test-btn.inverse:hover {
    background-color: #78cedd;
    color: #fff;
    transition: all .2s;
  }

  .test-btn.inverse:hover .arrow-right {
    border-top: 2px solid #fff;
    border-right: 2px solid #fff;
  }

  .test-btn.inverse .arrow-right {
    border-top: 2px solid #78cedd;
    border-right: 2px solid #78cedd;
  }

  .test-text {
    font-family: 'Helvetica-Roman', sans-serif;
    font-size: 27px;
    line-height: 37px;
    margin-bottom: 25px;
    color: #475461;
    @include desktop() {
      font-size: 24px;
      line-height: 1.4;
      margin-bottom: 16px;
    }
    @include laptop() {
      max-width: 360px;
      margin-left: auto;
      margin-right: auto;
    }
  }
</style>
