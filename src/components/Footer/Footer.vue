<template>
  <div>
    <div class="footerup">
      <!-- 底部具体内容盒子 -->
      <div class="footcont">
        <!-- 底部第一个盒子 -->
        <div class="fcontone">
          <div>
            <img src="https://static.shiyanlou.com/frontend/dist/img/4a4ab3d.svg" alt />
          </div>
          <div class="slogan">动手做实验，轻松学IT</div>
          <div class="social">
            <div class="wimg wx">
              <img src="../../assets/images/wx.svg" alt />
              <div class="wxewm">
                <img
                  class="ewmimg"
                  src="https://static.shiyanlou.com/frontend/dist/img/9f56dbd.png"
                  alt
                />
              </div>
            </div>

            <div class="wimg">
              <img src="../../assets/images/wb.svg" alt />
            </div>
          </div>
        </div>
        <!-- 底部第二个盒子 -->
        <div class="fconttwo">
          <div class="dctitle">公司</div>
          <p>关于我们</p>
          <p>联系我们</p>
          <p>加入我们</p>
        </div>
        <!-- 底部第三个盒子 -->
        <div class="fconttwo">
          <div class="dctitle">合作</div>
          <p>成为作者</p>
          <p>教师合作</p>
          <p>友情链接</p>
          <p>开发者</p>
        </div>
        <!-- 底部第四个盒子 -->
        <div class="fconttwo">
          <div class="dctitle">服务</div>
          <p>企业版</p>
          <p>实战训练营</p>
          <p>会员服务</p>
          <p>实验报告</p>
          <p>常见问题</p>
          <p>隐私条款</p>
        </div>
        <!-- 底部第五个盒子 -->
        <div class="fconttwo">
          <div class="dctitle">学习路径</div>
          <p>Python学习路径</p>
          <p>Linux学习路径</p>
          <p>大数据学习路径</p>
          <p>Java学习路径</p>
          <p>PHP学习路径</p>
          <p>全部</p>
        </div>
      </div>
    </div>
    <!-- 版权号 -->
    <div class="copyright">
      <span>Copyright @2013-2019 实验楼在线教育 |</span>
      <span class="spc">蜀ICP备13019762号</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  components: {},
  methods: {},
  mounted() {},
  watch: {},
  computed: {}
};
</script>

<style scoped lang='scss'>
.footerup {
  width: 100%;
  height: 215px;
  padding: 0;
  background-color: #333;
  // 底部盒子具体内容
  .footcont {
    display: flex;
    width: 73%;
    min-width: 1000px;
    margin: 0 auto;
    padding: 20px 15px;
    color: #999;
    // 底部第一个盒子
    .fcontone {
      width: 30.7%;
      padding: 0 10px;
      .slogan {
        padding: 13px 0;
        color: #0c9;
        font-size: 28px;
      }
      .social {
        display: flex;
        .wx {
          position: relative;
          // 微信二维码显示
          .wxewm {
            display: none;
            position: absolute;
            top: -75px;
            left: -60px;
            height: 70px;
            background-color: #1f2532;
            box-shadow: 0 5px 10px 0 rgba(0, 0, 0, 0.75);
            .ewmimg {
              width: 70px;
              height: 70px;
              // padding: 8px;
            }
          }
          &:hover .wxewm {
            display: block;
          }
        }
        .wimg {
          width: 32px;
          height: 32px;
          border-radius: 50%;
          background-color: #636469;
          margin-right: 30px;
          &:hover {
            cursor: pointer;
          }
          img {
            width: 100%;
            height: 100%;
            padding: 6px;
          }
        }
      }
    }
    // 底部盒子模板
    .fconttwo {
      width: 16.67%;
      padding: 0 10px;
      .dctitle {
        margin-bottom: 10px;
        font-size: 18px;
      }
      p {
        margin-bottom: 5px;
        font-size: 14px;
        &:hover {
          cursor: pointer;
          color: white;
        }
      }
    }
  }
}
// 版权号
.copyright {
  width: 100%;
  min-width: 1000px;
  padding: 15px 0;
  background-color: #191919;
  text-align: center;
  font-size: 12px;
  color: #666;
  .spc {
    margin-left: 5px;
    color: #999;
    &:hover {
      cursor: pointer;
      text-decoration: underline;
    }
  }
}
</style>