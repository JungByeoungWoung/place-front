<template>
    <div>
      <NavigationBar />
    <div class="row">
      <div class="col-md-6 mt-5 mx-auto">
        <form method="post" @submit.prevent="userRegister">
          <h2 class="h3 mb-3 font-weight-normal">회원가입</h2>
            <div class="form-grop">
              <label for="userID">유저 ID</label>
              <input id="userID" v-model="userID" type="text" name="userID" placeholder="유저아이디를 입력하세요" class="form-control">
            </div>
             <div class="form-group mb-3">
                  <span class="badge badge-danger mt-1" v-if="!userIdCheck">사용 불가능한 ID 입니다.</span>
               </div>
            <br>
             <div class="col">
               <button id="checkId" @click="checkUserId" type="button" class="btn btn-lg btn-primary btn-block">중복 확인</button>
             </div>
             <br>
            <div>
              <label for="userPwd">비밀번호</label>
              <input id="userPwd" v-model="userPwd" type="text" name="userPwd" placeholder="비밀번호를 입력하세요" class="form-control">
            </div>
            <div>
              <label for="userName">유저명</label>
              <input id="userName" v-model="userName" type="text" name="userName" placeholder="유저명을 입력하세요" class="form-control">
            </div>
            <div>
              <label for="email">email</label>
              <input id="email" v-model="email" type="text" name="email" placeholder="이메일을 입력하세요" class="form-control">
            </div>
            <!-- <div>
        <label for="userAddress">주소</label>
        <input type="text" id="userAddress" name="userAddress" placeholder="주소를 입력하세요" class="form-control">
      </div> -->
           <hr class="my-4">
            <div class="row">
              <div class="col">
                  <button onclick="location.href='/'" type="button" class="btn btn-lg btn-primary btn-block">취소</button>
                </div>
              <div class="col">
                <button id="registUser" type="submit" class="btn btn-lg btn-primary btn-block">유저 등록</button>
              </div>
            </div>
          </form>
      </div>
        
      </div>
    </div>
</template>

<script>
import { creaetLog } from '~/utils/userUtil';
export default {
  data() {
    return {
      result: {},
      userID: '',
      userPwd: '',
      userName: '',
      email: '',
      userAddress: '',
      userIdCheck: Boolean,
    }
   },
  methods: {
    async userRegister() {
      this.userIdCheck = true;
      try {
        const param = {
          userID: this.userID,
          userPwd: this.userPwd,
          userName: this.userName,
          email: this.email,
        };
        creaetLog('REQUEST PARAM', param);
        const result = await this.$axios.post('/user/userResist', param);
        creaetLog('회원 가입 결과', result.data);
        if (result.data.resultCode == '00') {
          alert('회원 가입이 완료 되었습니다.');
        } else {
          creaetLog('User Register Fail', result.data.resultMessage);
          alert('회원 가입 실패' +':'+ result.data.resultMessage);
         }
      } catch (e) {
        console.log(e);
      }
    },
    async checkUserId() { 
      try {
        const param = {
          userID: this.userID,
        }
        const result = await this.$axios.post('/user/userCheckId', param);
        creaetLog('중복 회원 결과', result.data.resultMessage);
        if (result.data.resultCode == '01') {
          this.userIdCheck = false;
        } else { 
          this.userIdCheck = true;
        }
      } catch (error) { 
        console.log(error);
      }
    },
  }
  
}
</script>