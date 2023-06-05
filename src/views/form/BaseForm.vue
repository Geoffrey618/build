<template>
    <div class="app-container">
        <div class="crumbs">
            <el-breadcrumb separator="/">
                <el-breadcrumb-item><i class="el-icon-date"></i>保修表单</el-breadcrumb-item>
                <el-breadcrumb-item>表单填写</el-breadcrumb-item>
            </el-breadcrumb>
        </div>
        <div class="container">
            <div class="form-box">
                <el-form ref="form" :model="form" label-width="80px">
                    <el-form-item label="报修问题">
                        <el-input v-model="form.id"></el-input>
                    </el-form-item>
                    <el-form-item label="报修类型">
                        <el-select v-model="form.region" placeholder="请选择">
                            <el-option key="bbk" label="设备维修" value="bbk"></el-option>
                            <el-option key="xtc" label="网络保修" value="xtc"></el-option>
                            <el-option key="imoo" label="其他类型" value="imoo"></el-option>
                        </el-select>
                    </el-form-item>
                    <el-form-item label="日期时间">
                        <el-col :span="11">
                            <el-date-picker type="date" placeholder="选择日期" v-model="form.date1" style="width: 100%;"></el-date-picker>
                        </el-col>
                    </el-form-item>
                    <el-form-item label="所在位置">
                        <el-cascader :options="options" v-model="form.options"></el-cascader>
                    </el-form-item>
                    <!-- <el-form-item label="选择开关">
                        <el-switch v-model="form.delivery"></el-switch>
                    </el-form-item> -->
                    <!-- <el-form-item label="多选框">
                        <el-checkbox-group v-model="form.type">
                            <el-checkbox label="步步高" name="type"></el-checkbox>
                            <el-checkbox label="小天才" name="type"></el-checkbox>
                            <el-checkbox label="imoo" name="type"></el-checkbox>
                        </el-checkbox-group>
                    </el-form-item> -->
                    <!-- <el-form-item label="单选框">
                        <el-radio-group v-model="form.resource">
                            <el-radio label="步步高"></el-radio>
                            <el-radio label="小天才"></el-radio>
                            <el-radio label="imoo"></el-radio>
                        </el-radio-group>
                    </el-form-item> -->
                    <el-form-item label="上传图片">
                      <el-upload class="upload-demo" :action="uploadUrl" :on-success="handleSuccess">
                        <el-button size="small" type="primary">上传图片</el-button>
                      </el-upload>
                    </el-form-item>
                    <el-form-item label="问题详述">
                        <el-input type="textarea" rows="3" v-model="form.desc"></el-input>
                    </el-form-item>
                    <el-form-item>
                        <el-button type="primary" @click="onSubmit">报修提交</el-button>
                        <el-button>取消</el-button>
                    </el-form-item>
                </el-form>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  data: function() {
    return {
      options: [
        {
          value: 'guangdong',
          label: '机场大厅'
        },
        {
          value: 'guangdong',
          label: 'T1航站楼',
          children: [
            {
              value: 'guangzhou',
              label: '一层',
              children: [
                {
                  value: 'tianhe',
                  label: '西区'
                },
                {
                  value: 'haizhu',
                  label: '东区'
                }
              ]
            },
            {
              value: 'dongguan',
              label: '二楼',
              children: [
                {
                  value: 'changan',
                  label: '西区'
                },
                {
                  value: 'humen',
                  label: '东区'
                }
              ]
            },
            {
              value: 'guangzhou',
              label: '三层',
              children: [
                {
                  value: 'tianhe',
                  label: '西区'
                },
                {
                  value: 'haizhu',
                  label: '东区'
                }
              ]
            },
            {
              value: 'guangzhou',
              label: '四层',
              children: [
                {
                  value: 'tianhe',
                  label: '西区'
                },
                {
                  value: 'haizhu',
                  label: '东区'
                }
              ]
            }
          ]
        },
        {
          value: 'hunan',
          label: 'T2航站楼',
          children: [
            {
              value: 'guangzhou',
              label: '一层',
              children: [
                {
                  value: 'tianhe',
                  label: '西区'
                },
                {
                  value: 'haizhu',
                  label: '东区'
                }
              ]
            },
            {
              value: 'dongguan',
              label: '二楼',
              children: [
                {
                  value: 'changan',
                  label: '西区'
                },
                {
                  value: 'humen',
                  label: '东区'
                }
              ]
            },
            {
              value: 'guangzhou',
              label: '三层',
              children: [
                {
                  value: 'tianhe',
                  label: '西区'
                },
                {
                  value: 'haizhu',
                  label: '东区'
                }
              ]
            },
            {
              value: 'guangzhou',
              label: '四层',
              children: [
                {
                  value: 'tianhe',
                  label: '西区'
                },
                {
                  value: 'haizhu',
                  label: '东区'
                }
              ]
            }
          ]
        }
      ],
      form: {
        name: '',
        region: '',
        date1: '',
        date2: '',
        delivery: true,
        type: ['步步高'],
        resource: '小天才',
        desc: '',
        options: []
      },
      uploadUrl: 'http://localhost:8000/api/upload', imageUrl: ''
    }
  },
  methods: {
    onSubmit() {
      this.$message.success('提交成功！')
    }
  }
}
</script>
