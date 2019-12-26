<template>
  <div>
    <div class="pcoursecont">
      <!-- 标题 -->
      <div class="pcoursetitle">
        <span class="sptitle">{{bigdate.classify_name}}</span>
        <span class="spmore">更多></span>
      </div>
      <div class="bigdate">
        <!-- 左边LOGO图片 -->
        <div class="leftimg">
          <img :src="this.bigdates.picture_url" alt />
        </div>
        <!-- 右边内容盒子 -->
        <div class="rightcontent">
          <div class="bigdatemodel" v-for="(item,index) in bigdate.courses" :key="index">
            <!-- 倍受好评 -->
            <div class="labe" v-if="item.label === '倍受好评'">
              <div>倍受好评</div>
              <div></div>
            </div>
            <!-- 云计算与大数据的课程图片 -->
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
  </div>
</template>

<script>
export default {
  data() {
    return {
      // 接收请求的后端开发的数据
      bigdate: [],
      bigdates: {}
    };
  },
  components: {},
  methods: {
    // 请求后端开发数据
    getBackend() {
      this.$axios
        .req("/classfication-courses")
        .then(res => {
          this.bigdate = res[4];
          this.bigdates = this.bigdate.recommend_course;
        })
        .catch(err => {
          console.log(err);
        });
    }
  },
  mounted() {
    this.getBackend();
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
  .bigdate {
    display: flex;
    width: 100%;
    // 左边LOGO盒子
    .leftimg {
      width: 22.76%;
      height: 525px;
      transition: all 0.5s;
      &:hover {
        cursor: pointer;
        box-shadow: 1px 2px 10px 1px #6c757d;
      }
      img {
        width: 100%;
        height: 100%;
      }
    }
    // 右边内容盒子
    .rightcontent {
      display: flex;
      justify-content: space-between;
      flex-wrap: wrap;
      width: 75%;
      margin-left: 2%;
      // 后端开发盒子模板
      .bigdatemodel {
        position: relative;
        z-index: 1;
        width: 31%;
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
        // 倍受好评
        .labe {
          div {
            &:nth-child(1) {
              position: absolute;
              top: 0;
              left: -8px;
              z-index: 2;
              padding: 1px 8px;
              color: #fff;
              background: #f66;
              font-size: 12px;
            }
            &:nth-child(2) {
              width: 10px;
              height: 10px;
              background: #de524d;
              position: absolute;
              top: 14px;
              left: -6px;
              z-index: -1;
              transform: rotate(45deg);
              border: 5px solid transparent;
              // transform: rotateX(90deg)
            }
          }
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
}
</style>