<template>
	<div>
		<router-link v-if="$route.path!=='/time-entries/log-time'" to="/time-entries/log-time" class="btn btn-primary">
			创建
		</router-link>
		<div v-if="$route.path==='/time-entries/log-time'">
			<h3>创建</h3>
		</div>
		<hr>
		<router-view v-on:updateTime='updateTime'></router-view>
		<div class="time-entries">
			<p v-if='!timeEntries.length'><strong>还没有计划</strong></p>
			<div class="list-group">
				<!-- v-for循环渲染 -->
				<a v-for="timeEntry in timeEntries" class="list-group-item">
					<div class="row">
						<div class="col-sm-2 user-details">
							<img :src="timeEntry.user.image" class="avatar img-circle img-respinsive" />
							<p class="text-center">
								<strong>{{ timeEntry.user.name }}</strong>
								{{ timeEntry.user.email }}
							</p>
						</div>
						<div class="col-sm-2 text-center time-block">
							<h3 class="list-group-item-text total-time"><i class="glyphicon glyphicon-time"></i>
								{{ timeEntry.totalTime }}
							</h3>
							<p class="label label-primary text-center">
								<i class="glyphicon glyphicon-calendar"></i>
								{{ timeEntry.date }}
							</p>
						</div>
						<div class="col-sm-7 comment-section">
						<p>
							{{ timeEntry.content }}
						</p>
						</div>
						<div class="col-sm-1">
							<button @click="deleteTimeEntry(timeEntry)" class="btn btn-xs btn-danger delete-button">X</button>
						</div>
					</div>
				</a>
			</div>
		</div>
	</div>
</template>
<script>
export default{
  data () {
    let exitEntries = {
      user: {
        name: 'YY',
        email: 'sudaimei@163.com',
        image: 'https://sfault-avatar.b0.upaiyun.com/888/223/888223038-5646dbc28d530_huge256'
      },
      content: '这是一个使用vue框架写的单应用页面',
      totalTime: 2,
      date: '2017-03-11'
    }
    return {
      timeEntries: [exitEntries]
    }
  },
  methods: {
    deleteTimeEntry (timeEntry) {
      let index = this.timeEntries.indexOf(timeEntry)
      this.timeEntries.splice(index, 1)
      this.$emit('deleteTime', timeEntry)
    },
    updateTime (timeEntry) {
      this.timeEntries.push(timeEntry)
      this.$emit('updateTime', timeEntry)
    }
  }
}
</script>
<style>
	.avatar{
		height: 75px;
		margin: 10px auto;
		display: block;
	}
	.user-details{
		background-color: #f5f5f5;
		border-right: 1px solid #ddd;
		margin: -10px 0;
	}
	.time-block{
		padding: 10px;
	}
	.comment-section{
		padding: 20px;
	}
	.list-group-item{
	    overflow: hidden;
	    margin-bottom: 20px;
	}
</style>
