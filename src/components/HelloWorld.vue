<template>
  <div class="hello">
    <h1>
      {{ msg }}
    </h1>
    <h1>
      {{ chirdMsg }}
      <!--获取父界面传过来的值-->
    </h1>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'my first vue project',
    }
  },
  props:['chirdMsg'],//获取父界面的值

}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
