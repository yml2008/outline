<template>
  <div id="app">
    <!-- <nav>
      <router-link to="/home" tag="span" active-class="active">首页</router-link>
      <router-link to="/reg" active-class="active" replace>注册</router-link>
      <router-link to="/login" active-class="active" event="mouseover">登录</router-link>
    </nav>-->
    <!-- <button @click="$router.back()">上一页</button>
    <button @click="$router.forward()">下一页</button>
    <nav>
      <ul>
        <li v-for="item in nav" :key="item.name" @click="goto(item)" :class="{active:item.path===current}">{{item.text}}</li>
      </ul>
    </nav>
    <h4>router-view显示路由内容</h4>-->
    <el-row style="height:61px;overflow:hidden;background-color:#545c64">
      <el-col :span="18">
        <el-menu
          mode="horizontal"
          background-color="#545c64"
          text-color="#fff"
          active-text-color="#ffd04b"
          :default-active="current"
          router
        >
          <el-menu-item :index="item.path" v-for="item in nav" :key="item.name">
            <i :class="item.icon"></i>
            {{item.text}}
          </el-menu-item>
        </el-menu>
      </el-col>
      <el-col :span="6" style="border-bottom:solid 1px #e6e6e6;height:61px;overflow:hidden;text-align:right;line-height:61px;padding-right:20px;">
        <el-button type="text" @click="goto('/reg')">注册</el-button>
        <el-button type="text" @click="goto('/login')">登录</el-button>
      </el-col>
    </el-row>
    <!-- <button @click="$router.push({name:'cart',params:{a:10,b:20}})">购物车</button> -->
    <!-- <keep-alive> -->
    <router-view />
    <!-- </keep-alive> -->
    <!-- <div class="left">
      <router-view name="left" />
    </div>
    <div class="main">
      <router-view name="main" />
    </div> -->
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      nav: [
        {
          name: "home",
          path: "/home",
          text: "首页",
          icon: "el-icon-s-home"
        },
        {
          name: "discover",
          path: "/discover",
          text: "发现",
          icon: "el-icon-view"
        },
        {
          name: "cart",
          path: "/cart",
          text: "购物车",
          icon: "el-icon-shopping-cart-2"
        }
        // {
        //   name: "login",
        //   path: "/login",
        //   text: "登录",

        // },
        // {
        //   name: "reg",
        //   path: "/reg",
        //   text: "注册"
        // }
      ],
      current: "/home"
    };
  },
  // 监听数据：监听实例的属性
  watch: {
    // 监听路由变化，实现高亮效果
    "$route.path": function(newVal) {
      // console.log(newVal, oldVal);
      this.current = newVal;
    }
  },
  methods: {
    goto(path) {
      // 编程式导航
      // this.$router.push(item.path);
      this.$router.replace(path);
    }
  },
  components: {},
  created() {
    let { path } = this.$route;
    this.current = path;
  }
};
</script>

<style lang="scss">
body{
  margin:0;
}
.price{
  span::before,del::before{
    content:'￥'
  }
  del{color:#999}
  span{color:#f00}
}
@for $i from 1 to 6{
  .m-#{$i}{
    margin:$i*0.3em;
  }
  .p-#{$i}{
    padding:$i*0.3em;
  }
}

nav a {
  margin: 0 10px;
}
.active {
  color: #f00;
  font-weight: bold;
}
</style>
