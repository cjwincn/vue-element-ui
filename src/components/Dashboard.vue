<template>
  <el-row class="warp">
    <el-col :span="24" class="warp-main">
      <section class="chart-container">
        <el-row class='margin-beside'>
          <el-col :span="8" v-for="(item, index) in detail">
            <el-card :body-style="{ padding: '0px' }">
              <a href='detail'><img src="../assets/images/forest.png" class="image"></a>
              <div style="padding: 14px;">
                <span>{{ item.description }}</span>
                <div class="bottom clearfix">
                  <time class="time">{{ item.time }}</time>
                </div>
              </div>
            </el-card>
          </el-col>
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

  .margin-beside {
    margin-left: 8%;
    margin-right: 20%;
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
        detail: [
          {
            description: '1231231313',
            time: new Date(),
            goodCount: 10,
            seeCount: 456,
            src: 'https://b-ssl.duitang.com/uploads/item/201602/19/20160219145658_JSKCZ.jpeg'
          },
          {
            description: '1231231313',
            time: new Date(),
            goodCount: 10,
            seeCount: 456,
            src: 'https://b-ssl.duitang.com/uploads/item/201602/19/20160219145658_JSKCZ.jpeg'
          },
          {
            description: '1231231313',
            time: new Date(),
            goodCount: 10,
            seeCount: 456,
            src: 'https://b-ssl.duitang.com/uploads/item/201602/19/20160219145658_JSKCZ.jpeg'
          },
          {
            description: '1231231313',
            time: new Date(),
            goodCount: 10,
            seeCount: 456,
            src: 'https://b-ssl.duitang.com/uploads/item/201602/19/20160219145658_JSKCZ.jpeg'
          },
          {
            description: '1231231313',
            time: new Date(),
            goodCount: 10,
            seeCount: 456,
            src: 'https://b-ssl.duitang.com/uploads/item/201602/19/20160219145658_JSKCZ.jpeg'
          },
          {
            description: '1231231313',
            time: new Date(),
            goodCount: 10,
            seeCount: 456,
            src: 'https://b-ssl.duitang.com/uploads/item/201602/19/20160219145658_JSKCZ.jpeg'
          }

        ]
        // chartColumn: null,
        // chartBar: null,
        // chartLine: null,
        // chartPie: null
      };
    },
    methods: {

    }
  }
</script>
