<template>
  <div class="all">
    <el-form :model="danbaiform" ref="danbaiform" class="demo-danbaiform">
      <h4>一、数据处理及误差分析（共85分）</h4>
      <div class="addmargin">
        <el-form-item>
          1. 周期的计算 :
          <input
            type="number"
            v-model="danbaiform.zq"
            class="border:none;outline: none;"
          />（保留三位小数，5分）
        </el-form-item>
      </div>
      <div class="addmargin">
        <p class="addmargin">
          2. 摆长的计算 : <br />
          钢球直径的测量数据如下表：(保留三位小数，每空3分，共42分)
        </p>
        <table border=" 1 " cellspacing="0 " style="width: 675px" class="table">
          <tr>
            <th style="width: 172px">测量次数</th>
            <th style="width: 172px">每次数据 d (cm)</th>
            <th style="width: 172px">
              平均值
              <img
                src="https://xwysbucket-bed.oss-cn-hangzhou.aliyuncs.com/img/one.png"
                style="height: 25px"
              />(cm)
            </th>

            <th style="width: 172px">
              △d=|d-<img
                src="https://xwysbucket-bed.oss-cn-hangzhou.aliyuncs.com/img/one.png"
                style="height: 25px"
              />|(cm)
            </th>
          </tr>
          <tr>
            <th>1</th>
            <th><input type="number" v-model="danbaiform.dcm1" /></th>
            <th class="nobboder"><input type="number" /></th>
            <th><input type="number" v-model="danbaiform.sd1" /></th>
          </tr>
          <tr>
            <th>2</th>
            <th><input type="number" v-model="danbaiform.dcm2" /></th>
            <th class="notboder nobboder"><input type="number" /></th>
            <th><input type="number" v-model="danbaiform.sd2" /></th>
          </tr>
          <tr>
            <th>3</th>
            <th><input type="number" v-model="danbaiform.dcm3" /></th>
            <th class="notboder nobboder"><input type="number" /></th>
            <th><input type="number" v-model="danbaiform.sd3" /></th>
          </tr>
          <tr>
            <th>4</th>
            <th><input type="number" v-model="danbaiform.dcm4" /></th>
            <th class="notboder nobboder"><input type="number" /></th>
            <th><input type="number" v-model="danbaiform.sd4" /></th>
          </tr>
          <tr>
            <th>5</th>
            <th><input type="number" v-model="danbaiform.dcm5" /></th>
            <th class="notboder nobboder"><input type="number" /></th>
            <th><input type="number" v-model="danbaiform.sd5" /></th>
          </tr>
          <tr>
            <th>6</th>
            <th><input type="number" v-model="danbaiform.dcm6" /></th>
            <th class="notboder nobboder"><input type="number" /></th>
            <th><input type="number" v-model="danbaiform.sd6" /></th>
          </tr>
          <tr>
            <th class="norboder">
              <img
                src="https://xwysbucket-bed.oss-cn-hangzhou.aliyuncs.com/img/three.png"
                style="width: 50px; position: relative; left: 65px"
              />
            </th>
            <th class="nolboder"></th>
            <th class="notboder">
              <input readonly />
            </th>
            <th><input type="number" v-model="danbaiform.average_sd" /></th>
          </tr>
          <!-- 平均值框 -->
          <input
            type="number"
            v-model="danbaiform.average_dcm"
            style="border: 0px solid; background-color: rbg(1, 1, 1, 0)"
            class="average_dcm"
          />
        </table>
        则<img
          src="https://xwysbucket-bed.oss-cn-hangzhou.aliyuncs.com/img/one.png"
          style="height: 35px"
        />= <input type="number" v-model="danbaiform.average_d" />（2分）<br />
        <img
          src="https://xwysbucket-bed.oss-cn-hangzhou.aliyuncs.com/img/three.png"
          style="width: 50px"
        />=
        <input type="number" v-model="danbaiform.averages_dcm" />（2分）<br />
        <p class="addmargin">
          所以有效摆长为:L =<input
            type="number"
            v-model="danbaiform.l"
          />（保留2位小数，5分）
        </p>
      </div>
      <div>
        <p class="addmargin">3. 重力加速度的计算 （共29分）:</p>
        <!-- 输入文本 -->
        <textarea v-model="danbaiform.js"></textarea>
      </div>

      <h4>二、选择题（每题5分，共15分）</h4>
      <div>1. 用单摆测定重力加速度g时，下面哪些做法可以减小误差？( )</div>
      <el-form-item>
        <el-radio-group v-model="danbaiform.xz1">
          <el-radio label="A">A. 摆线长度不宜太长，取0.1m左右为宜</el-radio
          ><br />
          <el-radio label="B"
            >B. 因为周期跟摆球质量无关，所以摆球用木球或铁球都一样</el-radio
          ><br />
          <el-radio label="C">C. 测摆长必须从悬点到摆球球心</el-radio><br />
          <el-radio label="D">D. 测周期必须用n次全振动总时间除以n-1</el-radio>
        </el-radio-group>
      </el-form-item>
      <div>2. 实验中某同学每次的测定值都比其它同学偏大，其原因可能是( )</div>
      <el-form-item>
        <el-radio-group v-model="danbaiform.xz2">
          <el-radio label="A">A. 实验室处在高山上，离海平面太高</el-radio><br />
          <el-radio label="B">B. 单摆所用的摆球太重</el-radio><br />
          <el-radio label="C"
            >C. 测出n次全振动的时间为t，误作为(n＋1)次全振动的时间进行计算 </el-radio
          ><br />
          <el-radio label="D">D. 以摆球半径和摆线之和作为摆长来计算</el-radio>
        </el-radio-group>
      </el-form-item>
      <div>3.如果测得g值偏小，不可能原因是( )</div>
      <el-form-item>
        <el-radio-group v-model="danbaiform.xz3">
          <el-radio label="A">A. 测摆线长时摆线拉得过紧</el-radio><br />
          <el-radio label="B">B. 摆线上端悬点未固定好，摆动中出现松动</el-radio
          ><br />
          <el-radio label="C">C. 计算摆长时，忘记了加小球半径</el-radio><br />
          <el-radio label="D">D. 读单摆周期时，读数偏大</el-radio>
        </el-radio-group>
      </el-form-item>
      <el-form-item>
        <el-button class="btn" type="primary" @click="onsubmit('danbaiform')"
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
      danbaiform: {
        zq: "",
        average_d: "",
        average_sd: "",
        l: "",
        dcm1: "",
        sd1: "",
        dcm2: "",
        sd2: "",
        dcm3: "",
        sd3: "",
        dcm4: "",
        sd4: "",
        dcm5: "",
        sd5: "",
        dcm6: "",
        sd6: "",
        averages_dcm: "",
        average_dcm: "",
        js: "",
        xz1: "",
        xz2: "",
        xz3: "",
      },
    };
  },
  methods: {
    async onsubmit() {
      for (var key in this.danbaiform) {
        if (!this.danbaiform[key]) {
          this.$message.error("题目未做完！");
          return false;
        }
      }
      const { data: res } = await this.$http.post(
        "/api/danbai",
        this.danbaiform
      );
      if (res.code == 200) {
        this.$message.success("提交成功");
        localStorage.setItem("state2", 2);
        this.$router.push("/home");
      }
      if (res.code == 100) {
        this.$message.error("已提交，请勿重复操作！");
      }
    },
  },
};
</script>

<style scoped>
.nolboder {
  border-left: 0px solid;
}
.norboder {
  border-right: 0px solid;
}
.notboder {
  border-top: 0px solid;
}
.nobboder {
  border-bottom: 0px solid;
}
.addmargin {
  margin: 10px 0px;
}
textarea {
  width: 100%;
  height: 200px;
}
.table input {
  border: none;
  outline: none;
}
.average_dcm {
  position: absolute;
  width: 160px;
  top: 35px;
  left: 330px;
  height: 165px;
}
table {
  position: relative;
  width: 500px;
}
table,
td,
th {
  border: 0.2px solid rgb(15, 15, 15);
}
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
