<template>
  <div class="all">
    <el-form :model="oumubiaoform" ref="oumubiaoform" class="demo-oumubiaoform">
      <h4>一、实验数据记录与处理（共75分）</h4>

      <div class="addmargin">
        <p class="addmargin">1. 待改装微安表参数记录(每空5分，共15分)</p>

        <table border=" 1 " cellspacing="0 " style="width: 500px" class="table">
          <tr>
            <th>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 微安表表头满量程电流Ig
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
            </th>
            <th><input type="number" /></th>
            <th>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;μA&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
            </th>
          </tr>
          <tr>
            <th>表头内阻Rg</th>
            <th><input type="number" /></th>
            <th>Ω</th>
          </tr>
          <tr>
            <th>电池电压E</th>
            <th><input type="number" /></th>
            <th>V</th>
          </tr>
        </table>
        <div>
          <p class="addmargin">
            2.
            各电阻阻值设置计算(要求四舍五入精确到小数点后1位，每空5分，共45分)
          </p>
          <p class="addmargin">
            调零电阻R1计算（理论值）<br />
            根据电路图，单刀开关开启，短接红黑表笔，此时调零电阻计算公式为：R1=E/Ig-Rg，
          </p>
          <p class="addmargin">
            代入E=
            <input style="width: 70px" type="number" />
            V, Ig=<input style="width: 70px" type="number" /> μA, Rg=<input
              style="width: 70px"
              type="number"
            />
            Ω，
          </p>
          <p class="addmargin">
            计算出R1=
            <input style="width: 70px" type="number" />
            Ω
          </p>
          <p class="addmargin">
            调零电阻R2计算（理论值）<br />
            根据电路图，单刀开关闭合，红黑表笔接100Ω电阻，此时校准电阻计算公式为：R2=[0.00015×(R1+Rg)]/[(E-0.00015×(R1+Rg))/100-0.00015]，
          </p>
          <p class="addmargin">
            代入E=
            <input style="width: 70px" type="number" />
            V, Rg=<input
              style="width: 70px"
              type="number"
              v-model="oumubiaoform.xz1"
            />
            Ω，
          </p>
          <p class="addmargin">
            计算出R2=
            <input
              style="width: 70px"
              type="number"
            />
            Ω
          </p>
        </div>
        <p class="addmargin">
          3. 万用表改装设计实验数据记录表(每空5分，共15分，截图分值另计)
        </p>
        <table  cellspacing="0 " style="width: 650px" class="table">
          <tr>
            <th rowspan="4">欧姆表的改装设计</th>
            <th style="width: 70px">改装要求</th>
            <th colspan="3">量程比率×1Ω</th>
            <th style="width: 130px" rowspan="4">
              Rx表头测量数据截图，要求将Rx读数标记在图上（5分）
            </th>
          </tr>
          <tr>
            <th rowspan="2">改装计算</th>
            <th style="width: 100px">调零电阻R1=</th>
            <th><input type="number"  /></th>
            <th style="width: 50px">Ω</th>
          </tr>

          <tr>
            <th>校准电阻R2=</th>
            <th><input type="number" /></th>
            <th>Ω</th>
          </tr>
          <tr>
            <th>测量电阻</th>
            <th>Rx=</th>
            <th><input type="number" /></th>
            <th>Ω</th>
          </tr>
          <tr>
             <th colspan="6" class="nobboder">
              <p style="float: left; display: block; margin-left: 10px">
                实验电路连线截图（5分）
              </p></th>
          </tr>
          <tr>
            <th colspan="6" style="float: left; margin:10px;">

              <el-upload
                action="#"
                list-type="picture-card"
                :auto-upload="false"
              >
                <i slot="default" class="el-icon-plus"></i>
                <div slot="file" slot-scope="{ file }">
                  <img
                    class="el-upload-list__item-thumbnail"
                    :src="file.url"
                    alt=""
                  />
                  <span class="el-upload-list__item-actions">
                    <span
                      class="el-upload-list__item-preview"
                      @click="handlePictureCardPreview(file)"
                    >
                      <i class="el-icon-zoom-in"></i>
                    </span>
                    <span
                      v-if="!disabled"
                      class="el-upload-list__item-delete"
                      @click="handleDownload(file)"
                    >
                      <i class="el-icon-download"></i>
                    </span>
                    <span
                      v-if="!disabled"
                      class="el-upload-list__item-delete"
                      @click="handleRemove(file)"
                    >
                      <i class="el-icon-delete"></i>
                    </span>
                  </span>
                </div>
              </el-upload>
            </th>
          </tr>
        </table>
      </div>

      <h4>二、选择题（每题5分，共15分）</h4>
      <div>1. 关于使用万用表欧姆档测电阻的下列说法中正确的是( )</div>

      <img class="photo" src="https://liuru1.oss-cn-chengdu.aliyuncs.com/img/%E6%AC%A7%E5%A7%86%E8%A1%A8.png?Expires=1661336052&OSSAccessKeyId=TMP.3KdJkzVYbcmkFNirRm72Qwddo4Pg9T97LAHR5c8NbMGxLqg3TirGMW4F9FJn55pPm1Xx698U4HVyNUrTUWmn1RvCFD31QA&Signature=7xkJO6v8wL3d%2FSsJIA81wqaoaSc%3D" alt="" />
      <el-form-item>
        <el-radio-group v-model="oumubiaoform.xz1">
          <el-radio label="A">A. 测量阻值不同的电阻时必须重新调零</el-radio
          ><br />
          <el-radio label="B"
            >B. 测量电路中的某个电阻，不需要把该电阻与电路断开</el-radio
          ><br />
          <el-radio label="C"
            >C.
            测量电阻时，为了使测量准确，应当尽量使指针指在中心刻度的附近</el-radio
          ><br />
          <el-radio label="D"
            >D.
            如图为某同学的实验测量结果，指针在a位置处表示被测电阻的阻值为50Ω</el-radio
          >
        </el-radio-group>
      </el-form-item>
      <div>
        2.
        把一个量程为5mA的电流表改装成欧姆表Rx1档，电流表的内阻是50Ω，电池的电动势是1.5v，经过调零之后测电阻，当欧姆表指针指到满偏的3/4位置时，被测电阻的阻值是(
        )
      </div>
      <el-form-item>
        <el-radio-group v-model="oumubiaoform.xz2">
          <el-radio label="A">A. 50 Ω</el-radio><br />
          <el-radio label="B">B. 100 Ω</el-radio><br />
          <el-radio label="C">C. 16.7 Ω </el-radio><br />
          <el-radio label="D">D. 400 Ω</el-radio>
        </el-radio-group>
      </el-form-item>
      <div>3.关于欧姆表，下列说法正确的是( )</div>
      <el-form-item>
        <el-radio-group v-model="oumubiaoform.xz3">
          <el-radio label="A">A. 刻度盘上的刻度是均匀的</el-radio><br />
          <el-radio label="B">B. 指针指在最左边，表示待测电阻为零</el-radio
          ><br />
          <el-radio label="C">C. 指针指在最左边，表示待测电阻为无穷大</el-radio
          ><br />
          <el-radio label="D">D. 欧姆表可以精确的测量电阻</el-radio>
        </el-radio-group>
      </el-form-item>
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
        <el-button class="btn" type="primary" @click="onsubmit('oumubiaoform')"
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
      oumubiaoform: {},
       dialogImageUrl: '',
        dialogVisible: false,
        disabled: false
    };
  },
  methods: {
    // async onsubmit() {
    //   for (var key in this.oumubiaoform) {
    //     if (!this.oumubiaoform[key]) {
    //       this.$message.error("题目未做完！");
    //       return false;
    //     }
    //   }
    //   const { data: res } = await this.$http.post(
    //     "/api/danbai",
    //     this.oumubiaoform
    //   );
    //   if (res.code == 200) {
    //     this.$message.success("提交成功");
    //     localStorage.setItem("state2", 2);
    //     this.$router.push("/home");
    //   }
    //   if (res.code == 100) {
    //     this.$message.error("已提交，请勿重复操作！");
    //   }
    // },
     handleRemove(file) {
        console.log(file);
      },
      handlePictureCardPreview(file) {
        this.dialogImageUrl = file.url;
        this.dialogVisible = true;
      },
      handleDownload(file) {
        console.log(file);
      }

  },
};
</script>

<style scoped>
.photo {
  height: 100px;
  width: 200px;
  margin: 10px;
  margin-left: 80px;
  background-color: rgba(231, 231, 231, 0.663);
}
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
  width: 100px;
  border: none;
  outline: none;
}

table {
  position: relative;
  /* width: 500px; */
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
