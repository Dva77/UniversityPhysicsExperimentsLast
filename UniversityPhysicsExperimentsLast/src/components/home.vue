<template>
  <div class="main">
    <el-container class="home_container">
      <el-header>
        <div class="header">
          <img src="https://www.nsu.edu.cn/img/logo.png" alt="" />
          <div class="loginbtn" @click="login">
            退出登录&nbsp;<img
              style="width: 20px; position: absolute; top: 1.5px"
              src="../assets/退出.png"
              alt=""
            />
          </div>
        </div>
      </el-header>
    </el-container>
    <div class="innerBox">
      <div class="box">
        <div
          style="
            text-align: center;
            color: rgb(0, 0, 0);
            margin: 0 auto;
            position: relative;
          "
        >
          <font
            size="4"
            id="mess"
            :class="{ beblue: this.themes, bewith: !this.themes }"
            @click="selfmes"
            >个人信息</font
          >
          <font size="7"
            >&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</font
          >
          <font
            id="kaoshi"
            size="4"
            :class="{ beblue: this.thetest, bewith: !this.thetest }"
            @click="intotest"
            >在线考试</font
          >
        </div>

        <div class="form" v-show="istest">
          <el-form :model="Form" style="margin: 0 auto">
            <tr>
              <td>姓名</td>
              <td :model="Form.student_name">{{ Form.student_name }}</td>
            </tr>
            <tr>
              <td>学号</td>
              <td :model="Form.student_num">{{ Form.student_num }}</td>
            </tr>
            <tr>
              <td>学生层次</td>
              <td :model="Form.student_level">{{ Form.student_level }}</td>
            </tr>
            <tr>
              <td>年级</td>
              <td :model="Form.student_year">{{ Form.student_year }}</td>
            </tr>
            <tr>
              <td>专业</td>
              <td :model="Form.student_spec">{{ Form.student_spec }}</td>
            </tr>
            <tr>
              <td>班级</td>
              <td :model="Form.student_class">{{ Form.student_class }}</td>
            </tr>
          </el-form>
        </div>
        <div class="tiaozhuan" v-show="!istest">
          <input
            type="button"
            class="btn"
            @click="daxuewuli"
            value="大学物理实验"
          />
          <input type="button" class="btn" @click="danbai" value="单摆实验" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      Form: {
        student_name: "",
        student_num: "",
        student_level: "",
        student_year: "",
        student_spec: "",
        student_class: "",
      },
      istest: false,
      themes: false,
      thetest: true,
    };
  },
  created() {
    this.getmessage();
  },
  methods: {
    async getmessage() {
      const { data: res } = await this.$http.post("/api/selectstudent");

      if (res.code == 200) {
        localStorage.setItem("state1", res.data[0].state);
        localStorage.setItem("state2", res.data[0].state_danbai);
        this.Form = res.data[0];
      }
    },
    daxuewuli() {
      if (localStorage.getItem("state1") == 2) {
        this.$message.error("该实验已完成作答");
      } else {
        this.$router.push("/daxuewulishiyan");
      }
    },
    danbai() {
      if (localStorage.getItem("state2") == 2) {
        this.$message.error("该实验已完成作答");
      } else {
        this.$router.push("/danbai");
      }
    },
    intotest() {
      this.istest = false;
      this.themes = false;
      this.thetest = true;
    },
    selfmes() {
      this.istest = true;
      this.themes = true;
      this.thetest = false;
    },
    login() {
      window.localStorage.clear();
      this.$router.push("/login");
    },
  },
};
</script>

<style scoped>
.loginbtn {
  position: absolute;
  right: 30px;
  top: 20px;
  cursor: pointer;
  /* font-size: small; */
  color: #ffffff;
}
.btn:hover {
  background-color: #0094ff;
  color: #fff;
  width: 80.2%;
  /* box-shadow: 1px 1px 2px 2px #6d9fe1; */
  z-index: 2;
}
#kaoshi {
  display: block;
  width: 50%;
  /* float: left; */
  position: absolute;
  right: 0;
  top: 30px;
}
#mess {
  display: block;
  width: 50%;
  /* float: left; */
  position: absolute;
  left: 0;
  top: 30px;
}
tr {
  color: black;
  /* text-align: center; */

  display: block;
  margin: 0 auto;
  width: 70%;
  /* margin-top:30px; */
  padding: 10px;
  /* background-color: antiquewhite; */
}
tr > td:first-child {
  display: block;
  width: 40%;
  float: left;
  padding-left: 13%;
  /* background-color: #83b0eb; */
}
.el-input {
  border: 0;
}
.beblue {
  border-bottom: 3px solid !important;
  border-color: #83b0eb !important;
  /* border: 3px solid; */
  padding-bottom: 14px;

  box-shadow: 0px 9px 12px -10px #6d9fe1;
}
.beblue:hover {
  color: blue;
}
.bewith:hover {
  color: blue;
}
.bewith {
  border-bottom: 3px solid #ccc !important;
  padding-bottom: 14px;
  border-color: rgb(219, 218, 218) !important;
  /* display: block;
  width: 50%; */
}
.tiaozhuan {
  margin: 30px 0px;
}
.form {
  margin: 20px 0;
  /* text-align: center; */
}
.btn {
  width: 80%;
  border: 0.1px solid rgb(242, 242, 242);
  display: block;
  margin: 0 auto;
  background-color: #ffffff;
  /* margin-bottom: 5%; */
  font-size: medium;
  padding: 3px 20px;
}

.box {
  background-color: rgba(255, 255, 255, 0.89);
  margin: 5vw auto;
  width: 400px;
  height: 380px;
  /* border-radius: 10px; */
}
.el-input {
  width: 60%;
  margin-left: 20%;
  margin: 0;
}
/* .el-input__inner {
   border: 0!important;
} */
.lablecss {
  color: black;
  float: right;
}
.home_container {
  background-color: rgb(0, 127, 247);
}

.main {
  color: #fff;
  height: 100%;
  position: relative;
  background-image: url("../assets/homebg.png");
  background-size: 100%;
}

font {
  /* background-color: blue; */
  cursor: pointer;
}

.el-input__inner {
  background-color: rgba(255, 255, 255, 0.7);
  border-radius: 0;
  border: 1px solid #0094ff;
  color: rgba(0, 0, 0, 0.7);
}

.el-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.header {
  display: flex;
  align-items: center;
}

.header img {
  width: 180px;
}
</style>
