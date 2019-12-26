<template>
  <div>
    <div class="pcoursecont">
      <div class="rows">
        <div class="rowmodel" v-for="(item,index) in ctags" :key="index">
          <div class="tagimg">
            <img :src="item.imgurl" alt />
          </div>
          <p>{{item.msg}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // 循环标签的数组
      ctags: [
        {
          imgurl: "https://static.shiyanlou.com/frontend/dist/img/5940276.gif",
          msg: "丰富全面的计算机实验课程"
        },
        {
          imgurl: "https://static.shiyanlou.com/frontend/dist/img/8b66710.gif",
          msg: "在线编程环境，1秒启动"
        },
        {
          imgurl: "https://static.shiyanlou.com/frontend/dist/img/9600bd2.gif",
          msg: "每天一个项目课，丰富你的项目经验"
        },
        {
          imgurl: "https://static.shiyanlou.com/frontend/dist/img/7f21af6.gif",
          msg: "有效学习时间，真实记录你的代码生涯"
        }
      ]
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
.pcoursecont {
  width: 73%;
  min-width: 1000px;
  margin: 70px auto;
  .rows {
    display: flex;
    justify-content: space-between;
    .rowmodel {
      width: 23%;
      .tagimg {
        width: 168px;
        height: 168px;
        margin: 0 auto;
        img {
          width: 100%;
          height: 100%;
        }
      }
      p {
        width: 80%;
        margin: 10px auto 0;
        color: #666;
        text-align: center;
      }
    }
  }
}
</style>