<template>
  <div class="box">
    <div class="cell">
      <span class="title">社区运行状况</span>
    </div>
    <div class="cell">
      <p>注册会员：{{ data.member_max }} </p>
      <p>主题：{{ data.topic_max}} </p>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      api: '//www.v2ex.com/api/site/stats.json',
      data: {}
    }
  },

  // 钩子
  mounted: function() {
    this.getData();
  },

  methods: {
    getData: function() {
      this.$http.get(this.api).then(function(res){
        this.data = res.data;
      })
    }
  }
}
</script>

<style scoped>
  .box {
    background: rgb(250, 250, 250);
  }

  .cell {
    padding: 10px;
    font-size: 12px;
    line-height: 120%;
    text-align: left;
    border-bottom: 1px solid #e2e2e2;
  }

  .title {
    color: #ccc;
  }

  .box .cell p {
    padding-top: 10px;
    font-size:14px;
    font-weight: bold;
  }
</style>
