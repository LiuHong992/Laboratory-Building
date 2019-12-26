<template>
  <div>
    <!--头部-->
    <div class="header">
      <div class="headerleft">
        <img src="../../assets/images/logo.svg" alt class="logoimg" />
        <span>做实验，学编程</span>
      </div>
      <div class="headeright">
        <a href="#">企业版</a>
        <a href="#">学校版</a>
        <div class="login">
          <a href>登录</a>
        </div>
        <div class="register">
          <a href>注册</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  components: {},
  methods: {
  },
  mounted() {
    
  },
  watch: {},
  computed: {}
};
</script>

<style scoped lang='scss'>
/*头部*/
.header {
  position: relative;
  display: flex;
  width: 73%;
  min-width: 1000px;
  height: 85px;
  margin: 0 auto;
}

.headerleft {
  display: flex;
  width: 265px;
  height: 85px;
  line-height: 84px;
  font-size: 18px;
  color: #274a59;
}

.logoimg {
  width: 125px;
  height: 85px;
  margin-right: 5px;
  &:hover{
    cursor: pointer;
  }
}

.headeright {
  position: absolute;
  top: 18px;
  right: 0;
  display: flex;
  width: 290px;
  height: 50px;
  line-height: 52px;
  text-align: center;
  a:hover{
    color: #08bf91;
  }
}

.headeright a {
  width: 60px;
  height: 15px;
  line-height: 15px;
  margin: auto 0;
  color: #999;
}

.headeright a:first-child {
  border-right: 1px solid #999;
}

.login {
  width: 85px;
}

.login a:first-child {
  border: none;
  color: #08bf91;
}
.login a:first-child:hover{
  color: green;
}

.register {
  width: 85px;
  background: #08bf91;
}

.register a:first-child {
  border: none;
  color: #f9f9f9;
}
</style>