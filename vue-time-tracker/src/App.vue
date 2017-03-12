<template>
  <div id="wrapper">
    <nav class="navbar navbar-default">
      <div class="container">
        <a class="navbar-brand" href="#">
          <i class="glyphicon glyphicon-time"></i>
          计划板
        </a>
        <ul class="nav navbar-nav">
          <li><router-link to="/home">首页</router-link></li>
          <li><router-link to="/time-entries">计划列表</router-link></li>
        </ul>
      </div>
    </nav>
    <div class="container">
      <div class="col-sm-3">
        <sidebar :time="totalTime"></sidebar>
      </div>
      <div class="col-sm-9">
        <router-view v-on:updateTime="updateTime" v-on:deleteTime="deleteTime"></router-view>
      </div>
    </div>
  </div>
</template>
<script>
import Sidebar from '@/components/Sidebar'

export default {
  name: 'app',
  components: {
    Sidebar
  },
  data () {
    return {totalTime: 2}
  },
  methods: {
    deleteTime (timeEntry) {
      this.totalTime -= parseFloat(timeEntry.totalTime)
    },
    updateTime (timeEntry) {
      this.totalTime += parseFloat(timeEntry.totalTime)
    }
  }
}
</script>
