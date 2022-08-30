<template>
  <div class="all">
    <el-form :model="wanyongform" ref="wanyongform" class="demo-wanyongform">
      <h4>一、实验数据记录与处理</h4>
      <div class="addmargin">
        <el-form-item>
          1. 待改装微安表参数记录 : <br />
          微安表满量程电流Ig=
          <input type="number" /> mA； 表头内阻Rg=
          <input type="number" /> Ω；<br />
          电池电压E= <input type="number" /> V；
        </el-form-item>
      </div>
      <div class="addmargin">
        2. 各电阻阻值设置计算（计算结果要求保留1位小数）
        <p class="addmargin">⑴分流电阻R1计算：</p>
        仅闭合转换开关1，此时分流电阻计算公式为：

        <img
          class="photo"
          src="https://liuru1.oss-cn-chengdu.aliyuncs.com/img/20220824172615.png?Expires=1661336348&OSSAccessKeyId=TMP.3KdJkzVYbcmkFNirRm72Qwddo4Pg9T97LAHR5c8NbMGxLqg3TirGMW4F9FJn55pPm1Xx698U4HVyNUrTUWmn1RvCFD31QA&Signature=1dQZm0Q8VlaxZf3umtpBSLgpuaM%3D"
          alt=""
        />
        <br />
        带入Rg= <input type="number" /> Ω；Ig= <input type="number" /> mA；Im=
        <input type="number" /> mA； <br />
        计算出：R1= <input type="number" /> Ω；<br />
        接入待测电流，得到：Ix= <input type="number" /> mA；

        <p class="addmargin">
          为了后续改装电压档和欧姆档的方便，根据电路图，在扩程电流档实现后，可将整个电流扩程电路看作为：
        </p>
        内阻：Rn=Rg//R1 = <input type="number" /> Ω；量程Im=
        <input type="number" /> mA的电流表。<br />
        <p class="addmargin">⑵分压电阻R2计算：</p>
        仅闭合转换开关2，此时分压电阻计算公式为：<br />
        <img
          class="photo"
          src="https://liuru1.oss-cn-chengdu.aliyuncs.com/img/20220824174107.png?Expires=1661336321&OSSAccessKeyId=TMP.3KdJkzVYbcmkFNirRm72Qwddo4Pg9T97LAHR5c8NbMGxLqg3TirGMW4F9FJn55pPm1Xx698U4HVyNUrTUWmn1RvCFD31QA&Signature=oSJhp4QSDOKxIJqlQN4dcU6hLPA%3D"
          alt=""
        /><br />
        带入Vm= <input type="number" /> V；Im= <input type="number" /> A；Rn=
        <input type="number" /> Ω；<br />
        计算出R2= <input type="number" /> Ω；<br />
        接入待测电压，得到：Vx== <input type="number" /> V；

        <p class="addmargin">⑶调零电阻R3计算（理论值）：</p>
        根据电路图，仅闭合转换开关3，短接红黑表笔，此时调零电阻计算公式为：<br />
        <img
          class="photo"
          src="https://liuru1.oss-cn-chengdu.aliyuncs.com/img/20220824174515.png?Expires=1661336256&OSSAccessKeyId=TMP.3KdJkzVYbcmkFNirRm72Qwddo4Pg9T97LAHR5c8NbMGxLqg3TirGMW4F9FJn55pPm1Xx698U4HVyNUrTUWmn1RvCFD31QA&Signature=231V8P1j8dU9TIgcapzve6WPaxw%3D"
          alt=""
        />
        <br />
        带入E= <input type="number" /> V；Im= <input type="number" /> A；Rn=
        <input type="number" /> Ω；<br />
        计算出R3= <input type="number" /> Ω；

        <p class="addmargin">⑷校准电阻R4计算（理论值）：</p>
        根据电路图及此微安表表盘刻度，闭合转换开关3和单刀开关，红黑表笔接100Ω电阻。此时校准电阻计算公式为：
        <img
          class="photo"
          src="https://liuru1.oss-cn-chengdu.aliyuncs.com/img/20220824174715.png?Expires=1661336227&OSSAccessKeyId=TMP.3KdJkzVYbcmkFNirRm72Qwddo4Pg9T97LAHR5c8NbMGxLqg3TirGMW4F9FJn55pPm1Xx698U4HVyNUrTUWmn1RvCFD31QA&Signature=nAnIwpe7nXwQzvKTi79igCOS%2FhQ%3D"
          alt=""
        />
        <br />

        带入：E= <input type="number" /> V；I3= <input type="number" /> A；Rx=
        <input type="number" /> Ω； R3+Rn= <input type="number" /> Ω；<br />
        计算出R4= <input type="number" /> Ω；<br />
        接入待测电阻，得到Rx= <input type="number" /> Ω；
      </div>

      <h4>二、思考题</h4>
      <div>
        下图是小明同学根据万用表改装设计实验要求，搭建的电路测试实验截图，请问：
        <img
          src="https://liuru1.oss-cn-chengdu.aliyuncs.com/img/20220824175138.png?Expires=1661336179&OSSAccessKeyId=TMP.3KdJkzVYbcmkFNirRm72Qwddo4Pg9T97LAHR5c8NbMGxLqg3TirGMW4F9FJn55pPm1Xx698U4HVyNUrTUWmn1RvCFD31QA&Signature=o8dQh9bnl5pt%2Fe4o04BUHNd9dYk%3D"
          alt=""
        />
      </div>
      <p class="addmargin">1.指出图中各电阻箱的作用：</p>
      电阻箱1（ <input type="text" /> ） 电阻箱2 （
      <input type="text" /> ）<br />
      电阻箱3（ <input type="text" /> ） 电阻箱4 （ ）<br />
      A. 调零电阻 B. 分流电阻 C. 分压电阻 D. 校准电阻
      <p class="addmargin">2.判断 T or F</p>
      ①实验测试前，微安表未机械调零。<input type="text" /> <br />
      ②实验测试中，在测量电流时，应该将单刀开关断开。<input type="text" />
      <h4>线上资源</h4>
      <p class="addmargin">
        1）在线实验报告系统链接：
        <a href="http://180.76.111.200/#/login "
          >http://180.76.111.200/#/login</a
        >
      </p>
      <p class="addmargin">
        2）在线资源链接：<a href="FTP://ftp.cs.nsu.edu.cn/大学物理实验"
          >FTP://ftp.cs.nsu.edu.cn/大学物理实验</a
        >
      </p>
      <el-form-item>
        <el-button class="btn" type="primary" @click="onsubmit('wanyongform')"
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
      wanyongform: {},
    };
  },
  methods: {
    async onsubmit() {
      for (var key in this.wanyongform) {
        if (!this.wanyongform[key]) {
          this.$message.error("题目未做完！");
          return false;
        }
      }
      const { data: res } = await this.$http.post(
        "/api/danbai",
        this.wanyongform
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
.photo {
  height: 80px;
  margin: 10px;
  margin-left: 100px;
  background-color: rgba(231, 231, 231, 0.663);
}
.addmargin {
  margin: 10px 0px;
}

.average_dcm {
  position: absolute;
  width: 160px;
  top: 35px;
  left: 330px;
  height: 165px;
}

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
input {
  width: 70px;
}
</style>
