<template>
<div>
  <img src="https://media.wired.com/photos/5c9040ee4950d24718d6da99/master/pass/shoppingcart-1066110386.jpg" alt="LA" style="width:100%">
  <div class="signup-box">
    <h>Sign up</h>
        <section>
            <!--email-->
            <div class="user-box">
                <input type="email"  v-model="form.email"  required>
                <label>Email</label>
            </div>

            <!--username-->
            <div class="user-box">
                <input type="text"  v-model="form.username"  required>
                <label>Username</label>
            </div>

            <!--password-->
            <div class="user-box">
                <input type="password"  v-model="form.password"  required>
                <label>Password</label>
            </div>

            <!--confirm password-->
            <div class="user-box">
                <input type="password"  v-model="form.confirmpassword"  required>
                <label>Confirm Password</label>
            </div>
            <button @click="signUp"><strong>Sign Up</strong></button>
  </section>
  </div>
</div>
</template>

<script>
import AuthUser from '@/store/AuthUser'
import DataUsersAPI from '@/store/DataUsersAPI'
export default {
    data() {
        return {
            form: {
                username: '',
                password: '',
                confirmpassword: '',
                email: ''
            },
        }
    },
    methods: {
        clearForm() {
            this.form = {
                username: '',
                password: '',
                confirmpassword: '',
                email: ''
            }
        },
        async signUp(){
            // let res = await AuthService.register(this.form)
            if(this.form.password === this.form.confirmpassword){
                let res = await AuthUser.dispatch('signUp',this.form)
                if(res.success){
                    let paylaod = {
                      name: res.user.username,
                      Total_Buy: 0,
                      point_used: 0,
                    }
                    // await DataUsersAPI.dispatch("createDateUser",paylaod)
                    this.$swal("Sign up Success", `Welcome ${res.user.username}`, "success")
                    this.$router.push("/")
                } 
                else {
                    this.$swal("Sign up Failed", res.message, "error")
                }
            }
            else{
                this.$swal('Password is not match', '', "error")
            }
        }
    }
}
</script>

<style scoped lang="scss">



h {
  letter-spacing: 0.05em;
  font-size: 250%;
  font-family: inherit;
  width: 600;
  color: #3e403f;
}

.signup-box {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 35%;
  height: 70%;
  padding: 40px;
  transform: translate(-50%, -50%);
  background: rgba(185, 123, 123, 0.836);
  box-sizing: border-box;
  box-shadow: 0 15px 25px rgba(214, 104, 14, 0.6);
  border-radius: 10px;
  margin-top: 3%;
}


.signup-box .user-box {
  position: relative;
}

.signup-box .user-box input {
  width: 100%;
  padding: 10px 0;
  font-size: 16px;
  color: #fff;
  margin-bottom: 30px;
  border: none;
  border-bottom: 1px solid #fff;
  outline: none;
  background: transparent;
}

.signup-box .user-box label {
  position: absolute;
  top:0;
  left: 0;
  padding: 10px 0;
  font-size: 16px;
  color: #fff;
  pointer-events: none;
  transition: .5s;
}

.signup-box .user-box input:focus ~ label,
.signup-box .user-box input:valid ~ label {
  top: -20px;
  left: 0;
  color: #00f1fd;
  font-size: 12px;
}

section button{
  cursor: pointer;
  position: relative;
  display: inline-block;
  padding: 10px 20px;
  color: #000000;
  font-size: 16px;
  text-decoration: none;
  text-transform: uppercase;
  overflow: hidden;
  transition: .5s;
  margin-top: 12%;
  letter-spacing: 4px;
  width: 45%;
}

button:hover {
  background: #9362d3;
  color: rgb(255, 255, 255);
  border-radius: 5px;
  box-shadow: 0 0 5px #c300ff,
              0 0 25px #f7d43c,
              0 0 50px #03e9f4,
              0 0 100px #03e9f4;
}


</style>

