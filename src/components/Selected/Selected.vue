<template>
  <div>
    <div class="pcoursecont">
      <!-- 标题 -->
      <div class="pcoursetitle">
        <span class="sptitle">{{select.classify_name}} |</span>
        <span>{{select.description}}</span>
        <span class="spmore">更多></span>
      </div>
      <!-- 精品课程 -->
      <div class="selectrow">
        <!-- 精品课程LOGO -->
        <div class="selectimg">
          <img :src="this.recommendcourse.picture_url" alt />
        </div>
        <!-- 精品课程盒子模板 -->
        <div class="selectmodel" v-for="(item,index) in select.courses" :key="index">
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
              <div class="peoples">
                <img src="../../assets/images/people.svg" alt />
                <span>{{item.students_count}}</span>
              </div>
              <div class="member" v-if="item.fee_type === 'member'">会员</div>
              <div class="bootcamp" v-if="item.fee_type === 'bootcamp'">训练营</div>
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
      // 接收精品课程数据数组
      select: [],
      recommendcourse: {}
    };
  },
  components: {},
  methods: {
    // 请求精品课程数据方法
    getSelect() {
      this.$axios
        .req("/classfication-courses")
        .then(res => {
          this.select = res[0];
          this.recommendcourse = this.select.recommend_course;
        })
        .catch(err => {
          console.log(err);
        });
    }
  },
  mounted() {
    this.getSelect();
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
  // 精品课程
  .selectrow {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    // logo图片
    .selectimg {
      width: 48.8%;
      height: 250px;
      transition: all 0.5s;
      &:hover {
        box-shadow: 1px 2px 10px 1px #6c757d;
      }
      img {
        width: 100%;
        height: 100%;
      }
    }
    // 精品课程盒子模板
    .selectmodel {
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
      // 精品课程的课程图片
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
          top: 2px;
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
          justify-content: space-between;
          z-index: 999;
          width: 100%;
          height: 50px;
          font-size: 12px;
          background-color: white;
          .peoples {
            display: flex;
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
          // 会员
          .member {
            width: 40px;
            height: 20px;
            border-radius: 20px;
            padding: 3px 8px;
            margin: 13px 5px;
            background-color: orange;
            text-align: center;
            color: white;
          }
          // 训练营
          .bootcamp {
            width: 52px;
            height: 22px;
            border-radius: 20px;
            padding: 4px 8px;
            margin: 13px 5px;
            background-color: crimson;
            text-align: center;
            color: white;
          }
        }
      }
    }
  }
}
</style>