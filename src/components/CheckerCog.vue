<template>
 <div class="content">
  <h1>{{ name }}</h1>
  <input v-model="start" placeholder="Password"/>
  <button @click="check()">Check</button>
  <ul>
   <p>Security score: {{ numberResult }}</p>
   <p>Password secure: {{ boolResult }}</p>
  </ul>
 </div>
 <div class="footer">
  <p class="footer">
   {{ msg }}
  </p>
 </div>
</template>

<script>

import vulcheck from 'vulcheck';

export default {

  name: 'CheckerCog',
  props: [
    'name',
    'msg'
  ],

  data() {
    // Setting up the app-wide
    // variables.
    return {
       start: '',
       numberResult: '',
       boolResult: '',
       isVul: false
    };
  },

  methods: {

    check(){
        this.numberResult = vulcheck.passwordStrength(this.start).toString();
        this.boolResult = '';
        console.log(vulcheck.isSecure(this.start));
        if (vulcheck.isSecure(this.start) == true ) {
            this.boolResult = 'Yes';
        }
        else {
            this.boolResult = 'No';
            this.isVul = true;
        }
    }

  }  
}
</script>

<style lang="scss">
@font-face {
  font-family: 'DotMatrix';
  src: url('https://blckunicorn.art/assets/fonts/DotMatrix.ttf') format('truetype');
}
$headingFont: 'DotMatrix';
$mainColor: #C566F5;
$gradientColorOne: #6700FE;
$gradientColorTwo: #9F5EFF;
$fontColor: #FFFFFF;
$extraColor: #000000;
$headingFontSize: 40px;
$contenFontSize: 30px;
$stdPadding: 10px;
$stdBorderRadius: 25px;
html, body {
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  width: 100vw;
  height: 100vh;
  margin: 0px;
  padding: 0px;
  background-color: $mainColor;
}

div.content {
  display: block;
  margin: 0 auto;
  width: 80%;
  background: linear-gradient(
    45deg,
    $gradientColorTwo,
    $gradientColorOne
  );
  padding: $stdPadding;
  margin-top: 20vh;
  margin-bottom: 30px;
  border-radius: $stdBorderRadius;
  border: 3px solid $fontColor;
}
h1 {
  text-align: center;
  padding: 0px;
  margin-top: 0px;
  margin-left: 0px;
  margin-right: 0px;
  margin-bottom: $stdPadding;
  font-size: $headingFontSize;
  color: $fontColor;
  font-family: $headingFont;
}
input {
  width: 80%;
  margin: 0 auto;
  display: block;
  padding: 10px;
  margin-top: 0px;
  margin-bottom:$stdPadding;
  font-size: $contenFontSize;
  color: $fontColor;
  font-family: $headingFont;
  background-color: $gradientColorOne;
  border: 3px solid $fontColor;
  border-radius: $stdBorderRadius;
}

input:focus {
  outline: none;
}

button {
  margin: 0 auto;
  display: block;
  margin-bottom: 10px;
  margin-top: 0px;
  width: 83%;
  text-align: center;
  padding: $stdPadding;
  font-size: $contenFontSize;
  font-family: $headingFont;
  border: none;
  border-radius: $stdBorderRadius;
  background-color: $fontColor;
  color: $extraColor;
  transition-duration: 0.6s;
}

button:hover {
  color: $mainColor;
}

ul {
  margin: 0 auto;
  display: block;
  margin-top: 0px;
  margin-bottom: $stdPadding !important;
  width: 83%;
  padding: 0px;
}

p {
  font-family: $headingFont;
  color: $fontColor;
  font-size: $contenFontSize;
  padding-top: 0px;
  padding-bottom: $stdPadding;
  padding-right: 0px;
  padding-left: 0px;
  margin: 0px;
}

div.footer {
  width: 100vw;
  border-top: 3px solid $fontColor;
  border-bottom: none;
  border-right: none;
  border-left: none;
  bottom: 0;
  right: 0;
  left: 0;
  margin: 0px;
  padding: 10px;
  position: fixed;
  background-color: transparent;
}

p.footer {
  font-family: $headingFont;
  color: $fontColor;
  font-size: $contenFontSize;
  padding: 0px;
  margin: 0px;
  text-align: center;
  font-style: italic;
}



@media screen and (max-width: 800px){
  $headingFontSize: 30px;
  $contenFontSize: 25px;
  div.content {
    margin-top: 20vh;
  }
  h1 {
    font-size: $headingFontSize;
  }
  input {
    width: 80%;
    font-size: $contenFontSize;
  }
  button {
    width: 85%;
    font-size: $contenFontSize;
  }

  p {
    font-size: $contenFontSize;
  }
  p.footer {
    font-size: $contenFontSize;
  }
}
</style>