<!--
VCHECK by Alexander Abraham,
a.k.a. "The Black Unicorn", a.k.a. "Angeldust Duke".
Licensed under the MIT license.
-->

<template>

 <!--Importing the main component and mounting it to the body.-->
 <CheckerCog name="VCHECK" msg="VCHECK by Alexander Abraham."/>

</template>

<script>

// Importing the main component and registering it.
import CheckerCog from './components/CheckerCog.vue';
export default {
  name: 'App',
  components: {
    CheckerCog
  }
}

</script>

<style>
</style>
