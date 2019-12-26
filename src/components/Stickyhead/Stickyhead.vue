<template>
  <div>
    <div class="stickyhead">
      <div class="headcont">
        <img src="../../assets/images/logo.svg" alt class="logoimg" />
        <div class="classescontent">
          <div>
            <el-dropdown>
              <a href>
                课程
                <i class="el-icon-caret-bottom"></i>
                <el-dropdown-menu slot="dropdown">
                  <el-dropdown-item>全部课程</el-dropdown-item>
                  <el-dropdown-item>学习路径</el-dropdown-item>
                </el-dropdown-menu>
              </a>
            </el-dropdown>
          </div>
          <div>
            <a href>训练营</a>
          </div>
          <div>
            <a href>楼+</a>
          </div>
          <div>
            <el-badge value="hot" class="item">
              <a href>会员</a>
            </el-badge>
          </div>
          <el-dropdown>
            <div class="community">
              <a href>
                社区
                <i class="el-icon-caret-bottom"></i>
                <el-dropdown-menu slot="dropdown">
                  <el-dropdown-item>讨论</el-dropdown-item>
                  <el-dropdown-item>教程库</el-dropdown-item>
                  <el-dropdown-item>直播</el-dropdown-item>
                  <el-dropdown-item>比赛</el-dropdown-item>
                </el-dropdown-menu>
              </a>
            </div>
          </el-dropdown>
        </div>
        <div class="headeright">
          <a href="#">企业版</a>
          <a href="#">学校版</a>
          <!-- 搜索框 -->
          <el-input
            size="mini"
            placeholder="搜索 课程/问答"
            suffix-icon="el-icon-search"
            v-model="input1"
            class="stickyheads"
          ></el-input>
          <div class="login">
            <a href>登录</a>
          </div>
          <div class="register">
            <a href>注册</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input1:''
    };
  },
  components: {},
  methods: {},
  mounted() {},
  watch: {},
  computed: {}
};
</script>

<style scoped lang='scss'>
// 吸顶导航栏
.stickyhead {
  position: fixed;
  top: 0;
  z-index: 9999;
  width: 100%;
  height: 72px;
  background-color: #fff;
  // transition: all .5s;

  .headcont {
    display: flex;
    position: relative;
    width: 73%;
    min-width: 1000px;
    height: 100%;
    margin: 0 auto;
    .logoimg {
      width: 125px;
      height: 100%;
      margin-right: 5px;
      &:hover {
        cursor: pointer;
      }
    }
    .classescontent {
      position: relative;
      display: flex;
      justify-content: space-around;
      width: 364.5px;
      height: 65px;
      line-height: 65px;
      a {
        color: #3a3a3a;
      }
      a:hover {
        cursor: pointer;
        color: #08bf91 !important;
      }
      .community {
        width: 59px;
      }
    }
    .headeright {
      position: absolute;
      top: 18px;
      right: 0;
      display: flex;
      // width: 290px;
      height: 50px;
      line-height: 52px;
      text-align: center;
      a:hover {
        color: #08bf91;
      }
      .stickyheads {
        width: 190px !important;
        margin: 0;
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
    .login a:first-child:hover {
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
  }
}
</style>