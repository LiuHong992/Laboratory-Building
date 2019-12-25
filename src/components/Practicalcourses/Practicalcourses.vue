<template>
  <div>
    <div class="pcoursecont">
      <div class="pcoursetitle">
        <span class="sptitle">楼+ 实战课程 |</span>
        <span>定期开班，导师助教全程辅导，最快最优成长</span>
        <span class="spmore">更多></span>
      </div>
      <div class="row">
        <el-col :span="6" v-for="(item,index) in ljcourses" :key="index">
          <el-card shadow="hover">
            <img :src="item.picture_url" alt />
            <div class="rowdown">
              <p>{{item.title}}</p>
              <span>最近班次：{{item.open_time}}</span>
            </div>
          </el-card>
        </el-col>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // 接收楼+实战课程数据的数组
      ljcourses: []
    };
  },
  components: {},
  methods: {
    // 请求楼+实战课程数据
    getCourses() {
      this.$axios
        .req("/louplus")
        .then(res => {
          this.ljcourses = res.slice(0, 4);
        })
        .catch(err => {
          console.log(err);
        });
    }
  },
  mounted() {
    this.getCourses();
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
  .row {
    width: 100%;
    min-width: 1000px;
    display: flex;
    justify-content: space-between;
    img {
      width: 100%;
      height: 90px;
      border-radius: 8px 8px 0 0;
    }
    .rowdown {
      padding: 18px 10px 15px;
      font-size: 18px;
      p {
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
        color: #565656;
        margin-bottom: 5px;
      }
      span {
        color: #a4a4a4;
      }
    }
  }
}
</style>