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
            <div>1.测量改装表内阻的方法，正确的是( )。</div>
            <el-form-item prop="oneItem">
                <el-radio-group v-model="formTable.oneItem">
                    <el-radio label="A">A.电压法</el-radio>
                    <el-radio label="B">B.替代法</el-radio>
                    <el-radio label="C">C.等效法</el-radio>
                    <el-radio label="D">D.外推法</el-radio>
                </el-radio-group>
            </el-form-item>
            <!-- 选择题第二题 -->
            <div>2.以下关于电流表的表述正确的是( )。</div>
            <el-form-item prop="TwoItem">
                <el-radio-group v-model="formTable.TwoItem">
                    <el-radio label="A">A.电流表的内阻较小，如果误用电流表去测电压，有烧毁电表的风险</el-radio>
                    <el-radio label="B">B.电流表的档位决定了它可通过的最小电流</el-radio>
                    <el-radio label="C">C.电流表可以用于测量电压，而无需切换到电压测试档</el-radio>
                    <el-radio label="D">D.电流表的内阻越大越好</el-radio>
                </el-radio-group>
            </el-form-item>
            <!-- 选择题第三题 -->
            <div>3. 由于磁电式电表结构上的一些缺陷，使得电表在正常条件下测量依然存在误差。</div>
            <div>引起误差的主要原因有( )。</div>
            <el-form-item prop="ThreeItem">
                <el-radio-group v-model="formTable.ThreeItem">
                    <el-radio label="A">A.转动机构的摩擦</el-radio>
                    <el-radio label="B">B.弹簧的弹性线性不良</el-radio>
                    <el-radio label="C">C.磁场分布不均匀</el-radio>
                    <el-radio label="D">D.仪表盘刻度不精确</el-radio>
                    <el-radio label="E">E.以上都有</el-radio>
                </el-radio-group>
            </el-form-item>
            <!-- 选择题第四题 -->
            <div>4.标称电表满刻度时，改装的电表未满刻度或超过满刻度，这种情况扩程电阻是大还是小及其原因，以下描述不正确的是？</div>
            <el-form-item prop="FourItem">
                <el-radio-group v-model="formTable.FourItem">
                    <el-radio label="A">A.对于改装的电流表，未满刻度时，扩程电阻小，因其分流大；</el-radio>
                    <el-radio label="B">B.对于改装的电流表，超过满刻度时，扩程电阻大 ，因其分流小；</el-radio>
                    <el-radio label="C">C.对于改装的电压表，未满刻度时，扩程电阻大 ，因其分压大；</el-radio>
                    <el-radio label="D">D.对于改装的电压表，超过满刻度时，扩程电阻小 ，因其分压小；</el-radio>
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
        ThreeItem: '',
        FourItem: ''
      },
      rulesTable: {
        oneItem: [{ required: true, message: '请选择选项', trigger: 'change' }],
        TwoItem: [{ required: true, message: '请选择选项', trigger: 'change' }],
        ThreeItem: [{ required: true, message: '请选择选项', trigger: 'change' }],
        FourItem: [{ required: true, message: '请选择选项', trigger: 'change' }]
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
