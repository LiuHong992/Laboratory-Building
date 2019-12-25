<template>
  <div>
    <div class="pcoursecont">
      <div class="pcoursetitle">
        <span class="sptitle">{{recents.classify_name}} |</span>
        <span>{{recents.description}}</span>
        <span class="spmore">更多></span>
      </div>
      <el-carousel>
        <el-carousel-item class="recentwheel" v-for="(item,index) in recent" :key="index">
          <div class="recentmodel" v-for="(item0,index0) in item" :key="index0">
            <!-- 精品课程的课程图片 -->
            <div class="middleimg">
              <img :src="item0.picture_url" alt />
            </div>
            <div class="selectdown">
              <div class="hide">
                <p>{{item0.name}}</p>
                <span class="scspan">{{item0.description}}</span>
              </div>
              <div class="watchs">
                <img src="../../assets/images/people.svg" alt />
                <span>{{item0.students_count}}</span>
                <div class="member" v-if="item0.fee_type === 'member'">会员</div>
                <div class="bootcamp" v-if="item0.fee_type === 'bootcamp'">训练营</div>
                <div class="limitfree" v-if="item0.fee_type === 'limit_free'">限免</div>
              </div>
            </div>
          </div>
        </el-carousel-item>
      </el-carousel>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      recents: [],
      // 接收近期好课数据的数组
      recent: []
    };
  },
  components: {},
  methods: {
    // 请求近期好课数据方法
    getRecent() {
      this.$axios
        .req("/classfication-courses")
        .then(res => {
          this.recents = res[1];
          for (let i = 0; i < this.recents.courses.length; i += 4) {
            this.recent.push(this.recents.courses.slice(i, i + 4));
          }
        })
        .catch(err => {
          console.log(err);
        });
    }
  },
  mounted() {
    this.getRecent();
  },
  watch: {},
  computed: {}
};
</script>

<style scoped lang='scss'>
//模板
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
  .recentwheel {
    height: 255px;
    display: flex;
    justify-content: space-between;
    flex-wrap: nowrap;
    // box-shadow:  15px 0 15px -15px #6c757d;
  }
  // 精品课程盒子模板
  .recentmodel {
    width: 23.2%;
    height: 250px;
    margin-bottom: 20px;
    background-color: rgb(255, 255, 255);
    transition: all 0.5s;
    &:hover {
      cursor: pointer;
      box-shadow: 1px 2px 5px #6c757d;
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
        // 会员
        .member {
          width: 25px;
          height: 15px;
          border-radius: 20px;
          padding: 3px 8px;
          margin: 13px 0 13px 150px;
          background-color: orange;
          text-align: center;
          color: white;
        }
        // 训练营
        .bootcamp {
          width: 40px;
          height: 15px;
          border-radius: 20px;
          padding: 4px 8px;
          margin: 13px 0 13px 140px;
          background-color: crimson;
          text-align: center;
          color: white;
        }
        // 限免
        .limitfree {
          width: 25px;
          height: 15px;
          border-radius: 20px;
          padding: 3px 8px;
          margin: 13px 0 13px 150px;
          background-color: orange;
          text-align: center;
          color: white;
        }
      }
    }
  }
}
</style>