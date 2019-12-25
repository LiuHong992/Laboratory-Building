<template>
  <div>
    <div class="pcoursecont">
      <div class="pcoursetitle">
        <span class="sptitle">{{basics.classify_name}} |</span>
        <span>{{basics.description}}</span>
        <span class="spmore">更多></span>
      </div>
      <div class="bascice">
        <!-- 基本功模板盒子 -->
        <div class="basicmodel" v-for="(item,index) in basics.courses" :key="index">
          <!-- 精品课程的课程图片 -->
          <div class="middleimg">
            <img :src="item.picture_url" alt />
          </div>
          <div class="selectdown">
            <div class="hide">
              <p>{{item.name}}</p>
              <span class="scspan">{{item.description}}</span>
            </div>
            <div class="watchs">
              <img src="../../assets/images/people.svg" alt />
              <span>{{item.students_count}}</span>
            </div>
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
      // 接收基本功数据的数组
      basics: []
    };
  },
  components: {},
  methods: {
    // 请求基本功数据
    getBasic() {
      this.$axios
        .req("/classfication-courses")
        .then(res => {
          this.basics = res[2];
        })
        .catch(err => {
          console.log(err);
        });
    }
  },
  mounted() {
    this.getBasic();
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
  // 基本功
  .bascice {
    display: flex;
    justify-content: space-between;
    width: 100%;
    min-width: 1000px;
    // 基本功盒子模板
    .basicmodel {
      width: 23.2%;
      height: 250px;
      margin-bottom: 20px;
      background-color: rgb(255, 255, 255);
      transition: all 0.5s;
      &:hover {
        cursor: pointer;
        box-shadow: 1px 2px 10px 1px #6c757d;
      }
      // 课程详细信息展示（hover触发）
      &:hover .selectdown > .hide {
        transform: translateY(-61px);
        transition: all 0.5s;
      }
      // 基本功的课程图片
      .middleimg {
        width: 100%;
        img {
          width: 100%;
        }
      }
      .selectdown {
        position: relative;
        height: 80px;
        .hide {
          position: relative;
          top: 1px;
          height: 80px;
          background-color: white;
          transform: translateY(0);
          transition: all 0.5s;
          padding: 10px;
          color: #666;
          p {
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
            padding-top: 2px;
            margin-bottom: 8px;
          }
          .scspan {
            height: 50px;
            line-height: 17px;
            word-break: break-all;
            text-overflow: ellipsis;
            overflow: hidden;
            display: -webkit-box;
            -webkit-line-clamp: 3;
            -webkit-box-orient: vertical;
            font-size: 12px;
          }
        }
        // 学生人数小盒子
        .watchs {
          position: absolute;
          top: 45px;
          left: 0px;
          display: flex;
          z-index: 999;
          width: 100%;
          height: 50px;
          font-size: 12px;
          background-color: white;
          // 学生人数处小图标
          img {
            display: block;
            width: 20px;
            height: 20px;
            margin-top: 14px;
            margin-left: 10px;
          }
          // 学生人数
          span {
            margin-left: 5px;
            line-height: 48px;
          }
        }
      }
    }
  }
}
</style>