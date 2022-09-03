<template>
  <div class="all">
    <el-form
    :model="Form"
    :rules="rules"
    ref="Form"
    class="Form"
    >
      <h4>一、选择题</h4>

      <div>1.请根据示波器面板的使用要求,选择正确的选项</div>
      <div>(1)当显示波形线条太粗了,可以尝试使用( )使波形线条调整至适合宽度</div>
      <div>(2)在示波器测量1KHz方波校准信号时,读数不够1KHz,可以尝试( )校准</div>
      <div>(3)当波形不够稳定不断跳跃时,可以尝试使用( )使波形相对静止</div>
      <el-form-item prop="cone">
        <el-radio-group v-model="Form.cone">
          <el-radio label="A">A.辉度按钮</el-radio>
          <el-radio label="B">B.聚焦按钮</el-radio>
          <el-radio label="C">C.水平位移</el-radio>
          <el-radio label="D">D.垂直位移</el-radio>
          <el-radio label="E">E.扫描微调按钮</el-radio>
          <el-radio label="F">F.触发电平按钮</el-radio>
        </el-radio-group>
      </el-form-item>

      <div>2.利用示波器测量信号频率的优点是( ),但不足的是示波器内部时基( ),且( )</div>
      <el-form-item prop="ctwo">
        <el-radio-group v-model="Form.ctwo">
          <el-radio label="A">A. 精度不高</el-radio>
          <el-radio label="B">B. 示波器不能测量频率</el-radio>
          <el-radio label="C">C. 不能直接读数频率，使用周期读数换算到频率会引入误差</el-radio>
          <el-radio label="D">D. 可以直观的观察出波形</el-radio>
        </el-radio-group>
      </el-form-item>

      <div>3.使用李萨如图形测量信号频率实验过程中,信号波形选用( )波形；得到闭合稳定的图案时,两个信号的频率比是( );在两个信号的相位关系变化时,李萨如图形会发生( )</div>
      <el-form-item prop="cthree">
        <el-radio-group v-model="Form.cthree">
          <el-radio label="A">A.三角波</el-radio>
          <el-radio label="B">B.正弦波</el-radio>
          <el-radio label="C">C.方波</el-radio>
          <el-radio label="D">D.整数比</el-radio>
          <el-radio label="E">E.无理数之比</el-radio>
          <el-radio label="F">F.跳出示波器窗口</el-radio>
          <el-radio label="G">G.旋转</el-radio>
        </el-radio-group>
      </el-form-item>

      <h4>一、判断题</h4>
      <div>1.在使用示波器的校准信号线校准示波器测量通道时,当示波器屏幕幅度读数不是5V时,可以通过调整"扫描微调旋钮"修正校准相应通道的读数( )</div>
       <el-form-item prop="one">
        <el-radio-group v-model="Form.one">
          <el-radio label="T">正确</el-radio>
          <el-radio label="F">错误</el-radio>
        </el-radio-group>
      </el-form-item>

      <div>2.只有正弦波信号才能利用本实验项目的李萨如图形方法测量频率( )</div>
      <el-form-item prop="two">
        <el-radio-group v-model="Form.two">
          <el-radio label="T">正确</el-radio>
          <el-radio label="F">错误</el-radio>
        </el-radio-group>
      </el-form-item>

      <div>3.在利用李萨如图形测量频率过程中,将示波器时基分度由默认的0.2ms/DIV改为0.1ms/DIV,则李萨如图形的纵横切点数之比会发生变化( )</div>
      <el-form-item prop="three">
        <el-radio-group v-model="Form.three">
          <el-radio label="T">正确</el-radio>
          <el-radio label="F">错误</el-radio>
        </el-radio-group>
      </el-form-item>

      <el-form-item>
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
          cone: "",
          ctwo: "",
          cthree: ""
        },
        rules: {
        one: [{ required: true, message: "请选择", trigger: "change" }],
        two: [{ required: true, message: "请选择", trigger: "change" }],
        three: [{ required: true, message: "请选择", trigger: "change" }],
        cone: [{ required: true, message: "请选择", trigger: "change" }],
        ctwo: [{ required: true, message: "请选择", trigger: "change" }],
        cthree: [{ required: true, message: "请选择", trigger: "change" }],
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
}
.btn {
  width: 20%;
  margin-left: 40%;
  margin-bottom: 2vw;
}
.el-radio-group {
  margin: 10px;
}
.el-radio {
  padding: 5px;
}
</style>
