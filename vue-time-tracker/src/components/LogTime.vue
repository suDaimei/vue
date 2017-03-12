<template>
	<div class="form-horizontal">
		<div class="form-group">
			<div class="col-sm-6">
				<label>日期</label>
				<input type="date" v-model="timeEntry.date" class="form-control" placeholder="Date">
			</div>
			<div class="col-sm-6">
				<label>时间</label>
				<input type="number" v-model="timeEntry.totalTime" class="form-control" placeholder="Hours">
			</div>
		</div>
		<div class="form-group">
			<div class="col-sm-12">
				<label>备注</label>
				<input type="text" v-model="timeEntry.content" class="form-control" placeholder="comment">
			</div>
		</div>
		<button @click="saveNewLog" class="btn btn-primary">保存</button>
		<router-link to="/time-entries" class="btn btn-danger">取消</router-link>
		<hr>
	</div>
</template>
<script>
export default{
  data () {
    return {
      timeEntry: {
        user: {
          name: 'hello',
          email: 'haha@163.com',
          image: 'https://sfault-avatar.b0.upaiyun.com/888/223/888223038-5646dbc28d530_huge256'
        }
      }
    }
  },
  methods: {
    saveNewLog () {
      let timeEntry = this.timeEntry
      this.$emit('updateTime', timeEntry)
      this.timeEntry = {
        user: {
          name: 'hello',
          email: 'haha@163.com',
          image: 'https://sfault-avatar.b0.upaiyun.com/888/223/888223038-5646dbc28d530_huge256'
        }
      }
    }
  }
}
</script>
