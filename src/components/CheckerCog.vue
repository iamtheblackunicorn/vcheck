<!--
VCHECK by Alexander Abraham,
a.k.a. "The Black Unicorn", a.k.a. "Angeldust Duke".
Licensed under the MIT license.
-->

<template>

 <!--Main Div displaying the main component.-->
 <div class="content">

  <!--Displays the heading.-->
  <h1>{{ name }}</h1>

  <!--Captures the data and processes it.-->
  <input v-model="start" placeholder="Password"/>
  <button @click="check()">Check</button>

  <!--Displays the computed results.-->
  <ul>
   <p>Security score: {{ numberResult }}</p>
   <p>Password secure: {{ boolResult }}</p>
   <p>Suggested password: {{ pwdSuggestion }}</p>
  </ul>

 </div>

 <!--A small footer for trademarking.-->
 <div class="footer">
  <p class="footer">
   VCheck on <a href="https://github.com/iamtheblackunicorn/vcheck">GitHub</a>
  </p>

 </div>

</template>

<script>

// Imports the vulcheck library for
// importing functions using my
// algorithm.
import vulcheck from 'vulcheck';

export default {

  // Naming the component.
  name: 'CheckerCog',

  // Exporting the needed
  // data.
  props: [
    'name',
    'appName'
  ],

  data() {

    // Setting up the app-wide
    // variables.
    return {
       start: '',
       numberResult: '',
       boolResult: '',
       pwdSuggestion: ''
    };
  },

  methods: {

    // Checking the input and suggesting a password if the password is deemed
    // to be to weak.
    check(){
        this.numberResult = vulcheck.passwordStrength(this.start).toString();
        this.boolResult = '';
        console.log(vulcheck.isSecure(this.start));
        if (vulcheck.isSecure(this.start) == true ) {
            this.boolResult = 'Yes';
            this.pwdSuggestion = '!NEEDED';
        }
        else {
            this.boolResult = 'No';
            this.pwdSuggestion = vulcheck.generatePassword(10);
        }
    }

  }  
}
</script>

<style lang="scss">

// Loading the remote font.
@font-face {
  font-family: 'DotMatrix';
  src: url('https://blckunicorn.art/assets/fonts/DotMatrix.ttf') format('truetype');
}

// Setting the app-wide variables.
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
$gradientColorThree: #FFC414;

/* DESKTOP SECTION START */
html, body {
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  width: 100vw;
  height: 100vh;
  margin: 0px;
  padding: 0px;
  background: linear-gradient(
   135deg,
   $mainColor,
   $gradientColorThree
  );
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
  background: linear-gradient(
   45deg,
   $mainColor,
   $gradientColorThree
  );
  color: $fontColor;
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
a {
  font-family: $headingFont;
  color: $fontColor;
  font-size: $contenFontSize;
  padding: 0px;
  margin: 0px;
  text-decoration: underline;
  transition-duration: 0.6s;
}
a:hover {
  color: $mainColor;
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
/* DESKTOP SECTION END */

/* MOBILE SECTION START */
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
/* MOBILE SECTION END */
</style>
