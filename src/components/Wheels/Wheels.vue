<template>
  <div>
    <!-- 轮播图主体 -->
    <el-carousel height="515px" arrow="always" class="headerwheel">
      <el-carousel-item
        :style="{background:item.background_color}"
        v-for="(item,index) in wheels"
        :key="index"
      >
        <img :src="item.picture_url" alt />
      </el-carousel-item>
    </el-carousel>
    <!-- 课程列表 -->
    <div class="courses">
      <ul class="courselist">
        <li
          v-for="(item,index) in courses"
          :key="index"
          @mouseenter="addNum(index)"
          @mouseleave="delNum"
        >
          <!-- 课程列表左边内盒子 -->
          <div class="innerdv">
            <span class="courseclass">{{item.name}}</span>
            <span class="coursetitle">{{item.tags[0].name}}</span>
            <span class="coursetitle">{{item.tags[1].name}}</span>
          </div>
          <!-- 课程列表浮动到课程名字上时右边显示的盒子 -->
          <div
            :style="{'top':show(index),'bottom':showb(index)}"
            class="outterdv"
            v-if="num === index"
          >
            <!-- 右边盒子上方内容 -->
            <div class="outup">
              <!-- 上方内容标题 -->
              <div class="title">
                <span class="iname">{{item.name}}</span>
              </div>
              <div class="upcontent">
                <div v-for="(item0,index0) in item.tags" :key="index0">{{item0.name}}</div>
              </div>
            </div>
            <!-- 右边盒子下方内容 -->
            <div class="outdown">
              <!-- 下方内容标题 -->
              <div class="title">
                <span>课程推荐</span>
              </div>
              <p v-for="(item1,index1) in item.recommend_courses" :key="index1">{{item1.name}}</p>
            </div>
          </div>
        </li>
        <div class="management">
          <span>经管专区</span>
        </div>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // 接收轮播图数据的数组
      wheels: [],
      // 接收课程列表数据的数组
      courses: [],
      num: -1
    };
  },
  components: {},
  methods: {
    // 获取轮播图数据
    getWheel() {
      this.$axios
        .req("/banner-pictures")
        .then(res => {
          this.wheels = res;
          // console.log(this.wheels);
        })
        .catch(err => {
          console.log(err);
        });
    },
    // 获取课程列表
    getCourse() {
      this.$axios
        .req("/categories")
        .then(res => {
          this.courses = res;
          // console.log(this.courses);
        })
        .catch(err => {
          console.log(err);
        });
    },
    addNum(idx) {
      this.num = idx;
    },
    delNum() {
      this.num = -1;
    },
    // 课程盒子前面几门课盒子定位方法
    show(idx) {
      if (idx === 0) {
        return 0;
      } else if (idx === 1) {
        return `57px`;
      } else if (idx > 1 && idx < 5) {
        return `84px`;
      }
    },
    // 课程盒子最后三门课盒子定位
    showb(idn) {
      if (idn >= 5) {
        return 0;
      }
    }
  },
  mounted() {
    this.getWheel();
    this.getCourse();
  },
  watch: {},
  computed: {}
};
</script>

<style scoped lang='scss'>
// 轮播图片属性
img {
  display: block;
  width: 73.3%;
  min-width: 1000px;
  margin: 0 auto;
}
// 课程列表
.courses {
  position: relative;
  z-index: 999;
  top: -515px;
  width: 73%;
  min-width: 1000px;
  height: 0;
  margin: 0 auto;
  .courselist {
    position: relative;
    width: 263px;
    height: 515px;
    background-color: rgba(0, 0, 0, 0.18);
    font-size: 14px;
    // 课程列表每一项的模板
    li {
      padding: 17px 12px 0;
      color: #fff;
      &:hover {
        color: darkgray;
        background-color: white;
      }
      // 课程列表左边内盒子
      .innerdv {
        height: 39px;
        border-bottom: 1px solid #bcbcbc;
        span:hover {
          cursor: pointer;
          color: #08bf91;
        }
        .courseclass {
          margin: 0 10px 0 5px;
        }
        .coursetitle {
          margin-right: 10px;
        }
      }
      // 课程列表浮动到课程名字上时右边显示的盒子
      .outterdv {
        position: absolute;
        left: 263px;
        z-index: 999;
        width: 400px;
        background-color: white;
      }
      // 内容标题
      .title {
        height: 40px;
        padding: 10px 15px;
        line-height: 40px;
        span {
          padding: 2px 5px;
          background-color: rgb(243, 239, 239);
          color: #777676;
        }
      }
      // 上方具体内容
      .upcontent {
        display: flex;
        padding: 5px 20px 20px 15px;
        flex-wrap: wrap;
        div {
          color: gray;
          padding: 0px 9px;
          margin: 5px 0;
          border-right: 1px solid gray;
          font-size: 12px;
          &:first-child {
            border-left: 1px solid gray;
          }
          &:hover {
            cursor: pointer;
            color: #08bf91;
          }
        }
      }
      // 下方具体内容
      .outdown {
        p {
          padding: 5px 17px;
          font-size: 12px;
          &:hover {
            cursor: pointer;
            color: #08bf91;
          }
          &:last-child {
            padding-bottom: 30px;
          }
        }
      }
    }
    // 经管专区
    .management {
      padding: 17px 12px 0;
      color: #fff;
      span {
        display: block;
        width: 80px;
        height: 29px;
        padding: 0 5px;
        margin: 0 auto;
        border-radius: 20px;
        border: 1px solid #fff;
        text-align: center;
        line-height: 30px;
        &:hover {
          cursor: pointer;
          color: rgb(29, 21, 21);
          background-color: white;
        }
      }
    }
  }
}
</style>