<template>
  <main id="main">
    <DiplomasHeader/>
  </main>
</template>

<script>
  import DiplomasHeader from './components/DiplomasHeader';

  export default {
    name: 'App',
    components: {
      DiplomasHeader,
    }
  }
</script>

<style>
  body {
    margin: 0;
    padding: 0;

    font-family: Rubik;
  }

  /* main#main {
  } */

  :root {
    --main-header: #B28DD6;
    --text-main-black: #000000;
    --color-lines-gray: #C4C4C4;
    --color-contrast-gray: #F9F9F9;
    --color-text-disabled: #989898;
    --white: #FFFFFF;
  }
</style>
