<template>
  <div id="firstcomponent">
     <h1>I am a title.</h1>
     <a> written by {{ author }} </a>
     <ol>
       <li v-for="n in evenNumbers">{{n}}</li>
     </ol>
  </div>
</template>

<script>
  export default {
    name: "firstcomponent",
    data() {
      return {
        numbers: [ 1, 2, 3, 4, 5 ],
        author: "微信公众号 jinkey-love"
      }
    },

    computed: {
      evenNumbers: function() {
        return this.numbers.filter(number => {
          return number%2 === 0;
        });
      }
    }
  }
</script>

<style>
</style>
