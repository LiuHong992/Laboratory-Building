<template>
  <div>
    <div class="pcoursecont">
      <!-- 标题 -->
      <div class="pcoursetitle">
        <span class="sptitle">训练营强化 |</span>
        <span>专注实战的完整项目，在实战中融会贯通</span>
        <span class="spmore">更多></span>
      </div>
      <!-- 训练营强化模板 -->
      <div class="strengmodel" v-for="(item,index) in strengthens" :key="index">
        <!-- 训练营图片 -->
        <div class="campimg">
          <img :src="item.picture_url" alt />
        </div>
        <!-- 训练营内容 -->
        <div class="campcont">
          <p class="pname">{{item.name}}</p>
          <p class="pcontent">{{item.description}}</p>
          <div class="campbottom">
            <span v-for="(item0,index0) in item.tags" :key="index0">{{item0}}</span>
            <div class="campdetails">查看详情</div>
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
      // 接收训练营强化数据的数组
      strengthens: []
    };
  },
  components: {},
  methods: {
    // 训练营强化数据方法
    getStreng() {
      this.$axios
        .req("/bootcamps")
        .then(res => {
          this.strengthens = res;
        })
        .catch(err => {
          console.log(err);
        });
    }
  },
  mounted() {
    this.getStreng();
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
  // 训练营强化模板
  .strengmodel {
    display: flex;
    width: 100%;
    margin-bottom: 20px;
    &:hover{
      cursor: pointer;
    }
    // 训练营图片
    .campimg {
      width: 40.13%;
      height: 250px;
      padding: 0 15px 0 0;
      img {
        width: 100%;
        height: 100%;
      }
    }
    // 训练营内容
    .campcont {
      width: 58%;
      padding: 15px;
      .pname {
        margin-bottom: 10px;
      }
      .pcontent {
        height: 103px;
        margin-top: 18px;
        font-size: 14px;
        color: #666;
      }
      .campbottom {
        position: relative;
        display: flex;
        height: 40px;
        margin-top: 30px;
        span {
          margin-right: 5px;
          font-size: 14px;
          color: #666;
          line-height: 60px;
        }
        .campdetails {
          position: absolute;
          right: 0;
          height: 32px;
          padding: 4px 16px;
          background-color:#ff9717;
          color: white;
          font-size: 21px;
          line-height: 32px;
        }
      }
    }
  }
}
</style>