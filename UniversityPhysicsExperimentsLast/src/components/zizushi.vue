<template>
  <div class="all">
    <el-form
    :model="Form"
    :rules="rules"
    ref="Form"
    class="Form"
    >
      <h4>一、选择题</h4>
      <div>在使用箱式直流电桥测量电阻时，为什么选取的比例臂一般应使单电桥的四个测量盘尽可能用上？(  )</div>
      <el-form-item prop="one">
        <el-radio-group v-model="Form.one">
          <el-radio label="A">A. 测量盘必须全用上</el-radio>
          <el-radio label="B">B. 比例臂的选取与测量盘使用个数无关</el-radio>
          <el-radio label="C">C. 使用一个测量盘时，读出的测量值精度最高</el-radio>
          <el-radio label="D">D. 读出的测量值有效位数多，测量精度有保证</el-radio>
        </el-radio-group>
      </el-form-item>
      <div>2.为了提高电桥测量的灵敏度，应采取哪些措施?:(  )</div>
      <el-form-item prop="two">
        <el-radio-group v-model="Form.two">
          <el-radio label="A">A. 提高电源电压</el-radio>
          <el-radio label="B">B. 使用低灵敏度检流计</el-radio>
          <el-radio label="C">C. 比例臂可以随意选取</el-radio>
          <el-radio label="D">D. 不使用等臂电桥</el-radio>
        </el-radio-group>
      </el-form-item>
          <h4>一、判断题</h4>
      <div>因为电桥箱是设计生产精良的专业实验仪器，电桥箱中的检流计不用调零。( )</div>
       <el-form-item prop="pone">
        <el-radio-group v-model="Form.pone">
          <el-radio label="T">正确</el-radio>
          <el-radio label="F">错误</el-radio>
        </el-radio-group>
      </el-form-item>

      <div>2.在电阻值的测量过程中，只用按下内接检流计开关这一个开关。( )</div>
      <el-form-item prop="ptwo">
        <el-radio-group v-model="Form.ptwo">
          <el-radio label="T">正确</el-radio>
          <el-radio label="F">错误</el-radio>
        </el-radio-group>
      </el-form-item>


      <el-form-item class="footer">
        <el-button class="btn" type="primary" @click="send('Form')" 
          >提交</el-button
        >
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        Form: {
          one: "",
          two: "",
          pone: "",
          ptwo: "",
        },
        rules: {
          one: [{ required: true, message: "请选择", trigger: "change" }],
          two: [{ required: true, message: "请选择", trigger: "change" }],
          pone: [{ required: true, message: "请选择", trigger: "change" }],
          ptwo: [{ required: true, message: "请选择", trigger: "change" }],
        }
      }
    },
    methods: {
      send(formName) {
      this.$refs[formName].validate(async (valid) => {
        if (valid) {
          const { data: res } = await this.$http.post(
            "/api/completion1/completion1",
            this.ruleForm
          );
          if (res.code == 100) {
            this.$message.error("提交失败！");
          }
          if (res.code == 150) {
            this.$message.error("请勿重复提交！");
          }
          if (res.code == 200) {
            this.$message.success("提交成功！");
            localStorage.setItem("state1", 2);
            this.$router.push("/home");
          }
        } else {
          this.$message.error("题目未答完！");
          return false;
        }
      });
    },
    }
  }
</script>

<style scoped>
.all {
  height: 100%;
  width: 50%;
  min-width: 320px;
  margin: 0 auto;
  text-align: left;
}
.btn {
  width: 20%;
  margin-bottom: 2vw;
}
.footer {
  text-align: center;
}
.el-radio-group {
  margin: 10px;
}
.el-radio {
  padding: 5px;
}
</style>
