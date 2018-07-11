<template>
  <el-row class="warp">
    <el-col :span="24" class="warp-breadcrum">
      <el-breadcrumb separator="/">
        <el-breadcrumb-item :to="{ path: '/' }"><b>首页</b></el-breadcrumb-item>
      </el-breadcrumb>
    </el-col>

    <el-col :span="24" class="warp-main">
      <section class="chart-container">
        <el-row>
          <el-col :span="8">
            <el-card :body-style="{ padding: '0px' }">
              <img src="../assets/images/forest.png" class="image">
              <div style="padding: 14px;">
                <span>一个例子而已</span>
                <div class="bottom clearfix">
                  <time class="time">{{ currentDate }}</time>
                </div>
              </div>
            </el-card>
          </el-col>
          <el-col :span="8">
            <el-card :body-style="{ padding: '0px' }">
              <img src="../assets/images/sunrise.png" class="image">
              <div style="padding: 14px;">
                <span>我是一张卡片</span>
                <div class="bottom clearfix">
                  <time class="time">{{ currentDate }}</time>
                </div>
              </div>
            </el-card>
          </el-col>
          <el-col :span="8">
            <el-card :body-style="{ padding: '0px' }">
              <img src="../assets/images/sunshine.png" class="image">
              <div style="padding: 14px;">
                <span>快乐生活每一天</span>
                <div class="bottom clearfix">
                  <time class="time">{{ currentDate }}</time>
                </div>
              </div>
            </el-card>
          </el-col>
          <!--<el-col :span="12">-->
            <!--<div id="chartColumn" style="width:100%; height:400px;"></div>-->
          <!--</el-col>-->
          <!--<el-col :span="12">-->
            <!--<div id="chartBar" style="width:100%; height:400px;"></div>-->
          <!--</el-col>-->
          <!--<el-col :span="12">-->
            <!--<div id="chartLine" style="width:100%; height:400px;"></div>-->
          <!--</el-col>-->
          <!--<el-col :span="12">-->
            <!--<div id="chartPie" style="width:100%; height:400px;"></div>-->
          <!--</el-col>-->
          <!--<el-col :span="24">-->
            <!--<a href="http://echarts.baidu.com/examples.html" target="_blank" style="float: right;">more>></a>-->
          <!--</el-col>-->
        </el-row>
      </section>

    </el-col>
  </el-row>
</template>
<style>
  .time {
    font-size: 13px;
    color: #999;
  }

  .bottom {
    margin-top: 13px;
    line-height: 12px;
  }

  .image {
    width: 100%;
    display: block;
  }

  .clearfix:before,
  .clearfix:after {
    display: table;
    content: "";
  }

  .clearfix:after {
    clear: both
  }

  .chart-container {
    width: 100%;
  }
  .chart-container .el-col {
    padding: 30px 20px;
  }
</style>

<script>

  export default {
    data() {
      return {
        currentDate: new Date(),
        // chartColumn: null,
        // chartBar: null,
        // chartLine: null,
        // chartPie: null
      };
    },
    mounted: function () {
    }
  }
</script>
