<template>
  <div class="login">
      <div class="left">
          <div class="title">
              <img src="@/assets/img/loginLogo.png" alt="">
              <span class="titleName">黑马面面</span>
              <span class="titleLine">|</span>
              <span class="titleName2">用户登录</span>

          </div>
        <el-form :model="form" :rules="rules" ref="form">
            <el-form-item  prop="phone">
                <el-input prefix-icon="el-icon-user
" v-model="form.phone" placeholder="请输入手机号"></el-input>
            </el-form-item>
            <el-form-item prop="password">
                <el-input :show-password="true" prefix-icon="el-icon-lock
" v-model="form.password" placeholder="请输入密码" ></el-input>
            </el-form-item>
            <el-form-item prop="code">
               <el-row>
                 <el-col :span="16">
                     <el-input v-model="form.code" prefix-icon="el-icon-key" placeholder="请输入验证码">
                    </el-input>
                 </el-col>
                <el-col :span="8">
                    <img src="@/assets/img/key.jpg" class="key" alt="">
                </el-col>
                </el-row>           
            </el-form-item>
            <el-form-item>
                <el-button class="btn" type="primary" @click="loginClick">登录</el-button>
                <br>
                  <el-button class="btn" type="primary" @click="registerClick">注册</el-button>
            </el-form-item>
        </el-form>
      </div>
        <div class="right">
            <img src="@/assets/img/login_banner_ele.png" alt="">
        </div>
    <register ref="register"></register>

  </div>
</template>

<script>
import register from "./register.vue"
export default {
    name:'login',
    components:{
        register
    },
    data(){
        return {
            form:{
                phone:'',
                password:'',
                code:'',
                isCheck:''
            },
            rules:{
                phone:[{
                    required:true,message:'请输入手机号',trigger:"change"
                }],
                password:[{required:true,message:'请输入密码',trigger:'change'},
                {
                    min:6,
                    max:12,
                    message:'请输入6到12位长度密码',
                    trigger:'change'
                }],
                code:[
                    {required:true,message:'请输入验证码',trigger:"change"},
                    {
                        min:4,
                        max:4,
                        message:'请正确输入验证码',
                        trigger:'change'
                    }
                ]
            }
        }
    },
    mounted() {
        alert(process.env.VUE_APP_DEV)
    },
    methods:{
        loginClick(){
            this.$refs.form.validate(result => {
                this.$message.success(result+"");
            });
        },
        registerClick(){
            this.$refs.register.dialogFormVisible = true;
        }
    }
}
</script>

<style lang="less">
    .login {
        display: flex;
    justify-content: space-around;
    align-items: center;
    height: 100%;
    background: linear-gradient(
        225deg,
        rgba(20,147,250,1),
        rgba(1,198,250,1)
    );
    .left {
        width: 478px;
        height: 550px;
        background: rgba(245,245,245,1);
        padding: 43px;
    
    .title {
        margin-bottom: 20px;
        .titleName {
            font-size: 24px;
            font-weight: 400;
            color:rgba(12,12,12,1);
            margin-left: 15px;
            margin-right: 15px;
        }
        .titleLine {
            color:#ccc;
            font-size: 24px;
        }
        .titleName2 {
            font-size: 22px;
            margin-left: 15px;
        }
    }
    .key {
        width: 100%;
        height: 40px;
    }
    .btn {
        width: 100%;
    }
    .btn:nth-child(1) {
        margin-bottom: 26px;
    }
    }
    }
</style>