<template>
  <div id="app">
     <img src="./assets/logo.png">

    <!--将父页面的值传递到子页面-->
    <hello-world chirdMsg="谢谢大家"></hello-world>

    <!--父页面获取子页面的值配置-->
    <child-page v-on:child-do-btn="childBtn"/>
    <!--获取子页面值进行父页面显示-->
    <p>$emit child page say something: {{ childContent }}</p>

    <h1 v-text="title"></h1>


    <input v-model="newItem" v-on:keyup.enter="addItem"/>
    <ul>
      <li
        v-for="item in items"
        v-bind:class="[vclass, { finish: item.isFinish }]"
        v-on:click="btn(item);"
      >
        {{ item.label }}
      </li>
    </ul>


  </div>
</template>

<script>
  import HelloWorld from "./components/HelloWorld";
  import ChildPage from "./components/ChildPage";
  import Store from "./store";

  export default {
    data() {
      {
        return {
          title: "this is a todo list",
          vclass: "vclass",
          items: Store.fetch(),
          newItem: "",
          childContent: '',
        };
      }
    },

    //观察者：监听items的变化
    watch: {
      items: {
        handler: function (val) {
          Store.save(val);
        },
        //deep:true可改变原型链的值
        deep: true
      },
    },
    methods: {
      btn: function (item) {
        item.isFinish = !item.isFinish;
      },
      addItem: function () {
        console.log(this.newItem);
        this.items.push({
          label: this.newItem,
          isFinish: false
        });
        this.newItem = "";
      },
      //父页面获取子页面的值注册方法
      childBtn: function (msg) {
        //msg的参数由子页面的$emit('key','msg')第二个参数获得
        this.childContent = msg;
      }
    },
    components: {
      HelloWorld,
      ChildPage
    }
  };

</script>

<style>
  #app {
    font-size: 20px;
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  .finish {
    text-decoration: underline;
    color: red;
  }
</style>
