<template>
    <div class="allStyle">
        <el-form
            :model="formTable"
            :rules="rulesTable"
            ref="formTable"
            class="formTable"
        >
            <h4>一、选择题</h4>
            <!-- 选择题第一题 -->
            <div>1.在使用箱式直流电桥测量电阻时，为什么选取的比例臂一般应使单电桥的四个测量盘尽可能用上?</div>
            <el-form-item prop="oneItem">
                <el-radio-group v-model="formTable.oneItem">
                    <el-radio label="A">A.测量盘必须全用上</el-radio>
                    <el-radio label="B">B.比例臂的选取与测量盘使用个数无关</el-radio>
                    <el-radio label="C">C.使用一个测量盘时，读出的测量值精度最高</el-radio>
                    <el-radio label="D">D.读出的测量值有效位数多，测量精度有保证</el-radio>
                </el-radio-group>
            </el-form-item>
            <!-- 选择题第二题 -->
            <div>2.为了提高电桥测量的灵敏度，应采取哪些措施?</div>
            <el-form-item prop="TwoItem">
                <el-radio-group v-model="formTable.TwoItem">
                    <el-radio label="A">A.提高电源电压</el-radio>
                    <el-radio label="B">B.使用低灵敏度检流计</el-radio>
                    <el-radio label="C">C.比例臂可以随意选取</el-radio>
                    <el-radio label="D">D.不使用等臂电桥</el-radio>
                </el-radio-group>
            </el-form-item>
            <h4>二、判断题</h4>
            <!-- 判断题第一题 -->
            <div>1.因为电桥箱是设计生产精良的专业实验仪器，电桥箱中的检流计不用调零。</div>
            <el-form-item prop="POneItem">
                <el-radio-group v-model="formTable.POneItem">
                    <el-radio label="T">正确</el-radio>
                    <el-radio label="F">错误</el-radio>
                </el-radio-group>
            </el-form-item>
            <!-- 判断题第二题 -->
            <div>2.在电阻值的测量过程中，只用按下内接检流计开关这一个开关。</div>
            <el-form-item prop="PTwoItem">
                <el-radio-group v-model="formTable.PTwoItem">
                    <el-radio label="T">正确</el-radio>
                    <el-radio label="F">错误</el-radio>
                </el-radio-group>
            </el-form-item>
            <el-form-item>
                <el-button
                    class="submitButton"
                    type="primary"
                    plain
                    @click="submitForm('formTable')"
                >提交</el-button>
            </el-form-item>
        </el-form>
    </div>
</template>

<script>
export default {
  data () {
    return {
      formTable: {
        oneItem: '',
        TwoItem: '',
        POneItem: '',
        PTwoItem: ''
      },
      rulesTable: {
        oneItem: [{ required: true, message: '请选择选项', trigger: 'change' }],
        TwoItem: [{ required: true, message: '请选择选项', trigger: 'change' }],
        POneItem: [{ required: true, message: '请选择选项', trigger: 'change' }],
        PTwoItem: [{ required: true, message: '请选择选项', trigger: 'change' }]
      }
    }
  },
  methods: {
    submitForm (formName) {
      this.$refs[formName].validate(async (valid) => {
        if (valid) {
          alert('submit!')
        } else {
          console.log('error submit!!')
          return false
        }
      })
    }
  }
}
</script>

<style>

.allStyle {
    height: 100%;
    width: 50%;
    min-width: 320px;
    margin: 0 auto;
}

.el-radio{
    display: block;
    /* height: 20px; */
    width: 50%;
    /* line-height: 20px; */
    /* padding: 5px; */
    margin-top: 5px;
    margin-bottom: 5px;
    }

.el-radio-group {
    margin-top: 5px;
    margin-bottom: 5px;
}

.el-form-item__content .submitButton {
    width: 20%;
    display: block;
    margin:0 auto;
}
</style>
