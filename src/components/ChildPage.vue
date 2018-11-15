<template>
    <div id="childID">
      <h3>
        {{ childTitle }}
      </h3>
      <button v-on:click="chilPageBtn">$emit点击子页面，将子页值赋值给父页</button>

    </div>
</template>

<script>
    export default {
        name: "ChildPage",
        data(){
          return{
            childTitle: 'this is a childPage',
          }
        },
        methods:{
          chilPageBtn:function () {
            //$emit
            this.$emit('child-do-btn',this.childTitle);

          },

        }

    }
</script>

<style scoped>
  h3{
    color: darkred;
    font-weight: bold;
  }

</style>
