<template>
    <div>
      <el-tabs :tab-position="tabPosition" style="">
        <el-tab-pane label="文章日志">
          <el-card class="box-card">文章一</el-card>
          <el-card class="box-card">文章二</el-card>
          <el-card class="box-card">文章四</el-card>
          <el-card class="box-card">文章五</el-card>
        </el-tab-pane>
        <el-tab-pane label="添加文章">
          <el-form :inline="true" :model="form1" class="demo-form-inline">
            <el-form-item label="文章类型">
              <el-select v-model="form1.type" placeholder="请输入类型">
                <el-option label="技术" value="technology"></el-option>
                <el-option label="生活" value="life"></el-option>
                <el-option label="便签" value="memo"></el-option>
              </el-select>
            </el-form-item>
            <el-form-item label="文章标题">
              <el-input v-model="form1.title" placeholder="请输入标题"></el-input>
            </el-form-item>
          </el-form>
          <el-form ref="form" :model="form" label-width="80px">

            <el-form-item label="活动时间">
              <el-col :span="11">
                <el-date-picker type="date" placeholder="选择日期" v-model="form.date1" style="width: 100%;"></el-date-picker>
              </el-col>
              <el-col class="line" :span="2">-</el-col>
              <el-col :span="11">
                <el-time-picker type="fixed-time" placeholder="选择时间" v-model="form.date2" style="width: 100%;"></el-time-picker>
              </el-col>
            </el-form-item>

            <el-form-item label="活动形式">
              <el-input type="textarea" v-model="form.desc"></el-input>
            </el-form-item>
            <el-form-item>
              <el-button type="primary" @click="onSubmit">立即创建</el-button>
              <el-button>取消</el-button>
            </el-form-item>
          </el-form>
        </el-tab-pane>
      </el-tabs>
    </div>
</template>
<script>
  export default {
    components: {},
    data() {
      return {
        tabPosition: 'left',
        form1: {
          type: '',
          title: ''
        },
        form: {
          name: '',
          region: '',
          date1: '',
          date2: '',
          delivery: false,
          type: [],
          resource: '',
          desc: ''
        }
      }
    },
    methods: {
      onSubmit() {
        console.log('submit!')
      }
    }
  }
</script>
