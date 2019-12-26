<template>
  <div>
    <div class="pcoursecont">
      <!-- 标题 -->
      <div class="pcoursetitle">
        <span class="sptitle">学习路径 |</span>
        <span>精准而系统的学习路径，从0到大牛</span>
        <span class="spmore">更多></span>
      </div>
      <!-- 学习路径 -->
      <div class="routes">
        <!-- 学习路径模板 -->
        <div class="routemodel" v-for="(item,index) in routes" :key="index">
          <!-- 学习路径图片 -->
          <div class="routeimg">
            <img :src="item.image" alt />
          </div>
          <div class="hotimg" v-if="item.is_hot">
            <img src="../../assets/images/Hot.png" alt />
          </div>
          <div class="routetitle">{{item.name}}</div>
          <div class="routecourse">{{item.courses_count}}门课程</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // 接收学习路径数据的数组
      routes: []
    };
  },
  components: {},
  methods: {
    // 获取学习路径数据方法
    getRoute() {
      this.$axios
        .req("/paths")
        .then(res => {
          this.routes = res;
        })
        .catch(err => {
          console.log(err);
        });
    }
  },
  mounted() {
    this.getRoute();
  },
  watch: {},
  computed: {}
};
</script>

<style scoped lang='scss'>
.pcoursecont {
  width: 73%;
  min-width: 1000px;
  margin: 30px auto;
  // 标题
  .pcoursetitle {
    position: relative;
    margin-bottom: 30px;
    line-height: 30px;
    color: #666;
    .sptitle {
      padding: 0 8px 0 0;
      font-size: 24px;
    }
    .spmore {
      position: absolute;
      right: 0;
    }
  }
  // 学习路径
  .routes {
    display: flex;
    justify-content: space-between;
    width: 100%;
    // 学习路径模板
    .routemodel {
      position: relative;
      width: 23%;
      // height: 258px;
      text-align: center;
      background-color: white;
      box-shadow: 1px 1px 2px #c4c2c2;
      transform: translateY(0);
      transition: all 0.4s;
      // 学习路径盒子Hover效果
      &:hover {
        cursor: pointer;
        box-shadow: 1px 1px 6px 5px #c4c2c2;
        transform: translateY(-11px);
        transition: all 0.4s;
      }
      // 学习路径图片
      .routeimg {
        height: 130px;
        img {
          width: 100%;
          height: 100%;
        }
      }
      // hot图片
      .hotimg {
        position: absolute;
        top: 8px;
        right: -5px;
        width: 44px;
        height: 21px;
      }
      .routetitle {
        padding: 30px 0 15px;
        color: #666;
        font-size: 18px;
      }
      .routecourse {
        font-size: 14px;
        color: #a4a4a4;
        padding-bottom: 30px;
      }
    }
  }
}
</style>