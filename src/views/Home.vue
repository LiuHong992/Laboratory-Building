<template>
  <div id="bodys">
    <el-container>
      <el-header>
        <Headers></Headers>
        <!--头部导航栏-->
        <div class="menulist">
          <div class="classes">
            <a href="#">
              <img src="../assets/images/classes.svg" alt />
              <span>全部课程</span>
            </a>
          </div>
          <div class="classescontent">
            <div>
              <a href="#">路径</a>
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
            <!-- <div class="morecommunity">
              <div>讨论</div>
              <div>教程库</div>
              <div>直播</div>
              <div>比赛</div>
            </div>-->
          </div>
          <!-- 搜索框 -->
          <el-input
            size="mini"
            placeholder="搜索 课程/问答"
            suffix-icon="el-icon-search"
            v-model="input1"
          ></el-input>
        </div>
      </el-header>
      <el-main>
        <!-- 轮播图 -->
        <Wheels></Wheels>
        <!-- 楼+实战课程 -->
        <Pcourses></Pcourses>
        <!-- 精选项目课 -->
        <Selected></Selected>
        <!-- 近期好课 -->
        <Recent></Recent>
        <!-- 基本功 -->
        <Basic></Basic>
        <!-- 后端开发 -->
        <Backend></Backend>
        <!-- 云计算与大数据 -->
        <Bigdate></Bigdate>
      </el-main>
      <el-footer>Footer</el-footer>
    </el-container>
  </div>
</template>

<script>
import Headers from "../components/Header/Header";
import Wheels from "../components/Wheels/Wheels";
import Pcourses from '../components/Practicalcourses/Practicalcourses'
import Selected from '../components/Selected/Selected'
import Recent from '../components/Recentclass/Recentclass'
import Basic from '../components/Basicskill/Basicskill'
import Backend from '../components/Backend/Backend'
import Bigdate from '../components/Bigdate/Bigdate'
export default {
  data() {
    return {
      input1: ""
    };
  },
  components: {
    Headers,
    Wheels,
    Pcourses,
    Selected,
    Recent,
    Basic,
    Backend,
    Bigdate
  },
  methods: {},
  mounted() {
    // this.$axios.req('/categories').then(res => {
    //   console.log(res);
    // }).catch(err => {
    //   console.log(err);
    // })
  },
  watch: {},
  computed: {}
};
</script>

<style scoped lang='scss'>
#bodys {
  background: #f9f9f9;
}

/*头部导航栏*/
.menulist {
  position: relative;
  display: flex;
  width: 73%;
  min-width: 1000px;
  height: 65px;
  margin: 0 auto;
  background-color: white;
}

.classes {
  width: 263px !important;
  background: #08bf91;
}

.classes a {
  display: flex;
  width: 85px;
  text-indent: 20px;
  color: white;
  margin: 23px 18px;
}
.item {
  margin-right: 20px;
}
.classes span {
  text-align: center;
  text-indent: 5px;
  line-height: 18px;
}

.classescontent {
  position: relative;
  display: flex;
  justify-content: space-around;
  width: 364.5px;
  height: 65px;
  line-height: 65px;
  a:hover {
    cursor: pointer;
    color: #08bf91 !important;
  }
  .community {
    width: 59px;
  }
}
</style>