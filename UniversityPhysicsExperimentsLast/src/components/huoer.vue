<template>
  <div class="all">
    <el-form
    :model="Form"
    :rules="rules"
    ref="Form"
    class="Form"
    >
      <h4>一、选择题</h4>
      <div>1.若磁感应强度B与元件平面法线存在角度α时,作用在元件上的有效磁场大小为:(  )</div>
      <el-form-item prop="one">
        <el-radio-group v-model="Form.one">
          <el-radio label="A">A. Bcosa</el-radio>
          <el-radio label="B">B. Bsina</el-radio>
          <el-radio label="C">C. Btana</el-radio>
          <el-radio label="D">D. Bcota</el-radio>
        </el-radio-group>
      </el-form-item>
      <div>2.若磁感应强度B与工作电流方向存在角度β时,作用在元件上的有效磁场大小为:(  )</div>
      <el-form-item prop="two">
        <el-radio-group v-model="Form.two">
          <el-radio label="A">A. Bsinβ</el-radio>
          <el-radio label="B">B. Bcosβ</el-radio>
          <el-radio label="C">C. Btanβ</el-radio>
          <el-radio label="D">D. Bcotβ</el-radio>
        </el-radio-group>
      </el-form-item>
      <div>3.测量不等位电势差时,若不等位电势差不为0,则增大工作电流时,不等位电势差将:(  )</div>
      <el-form-item prop="three">
        <el-radio-group v-model="Form.three">
          <el-radio label="A">A. 增大</el-radio>
          <el-radio label="B">B. 减小</el-radio>
          <el-radio label="C">C. 不变</el-radio>
          <el-radio label="D">D. 不确定</el-radio>
        </el-radio-group>
      </el-form-item>
      <div>4.若磁感应强度B与元件平面法线存在角度α,与工作电流方向存在角度β时,作用在元件上的有效磁场大小为:(  )</div>
      <el-form-item prop="four">
        <el-radio-group v-model="Form.four">
          <el-radio label="A">A. Bcosasinβ</el-radio>
          <el-radio label="B">B. Bcosacosβ</el-radio>
          <el-radio label="C">C. Bsinasinβ</el-radio>
          <el-radio label="D">D. Bsinacosβ</el-radio>
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
          three: "",
          four: "",
        },
        rules: {
        one: [{ required: true, message: "请选择", trigger: "change" }],
        two: [{ required: true, message: "请选择", trigger: "change" }],
        three: [{ required: true, message: "请选择", trigger: "change" }],
        four: [{ required: true, message: "请选择", trigger: "change" }],
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
.footer {
  text-align: center;
}
.btn {
  width: 20%;
  margin-bottom: 2vw;
}
.el-radio-group {
  margin: 10px;
}
.el-radio {
  padding: 5px;
}
</style>
