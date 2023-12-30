<template>
    <div>
      <NavigationBar />
    <div class="row">
      <div class="col-md-6 mt-5 mx-auto">
        <form method="post" @submit.prevent="userRegister">
          <h2 class="h3 mb-3 font-weight-normal">회원가입</h2>
            <div class="form-grop">
              <label for="userId">유저 ID</label>
              <input id="userId" type="text" name="userId" placeholder="유저아이디를 입력하세요" class="form-control">
            </div>
            <div>
              <label for="userPwd">비밀번호</label>
              <input id="userPwd" type="text" name="userPwd" placeholder="비밀번호를 입력하세요" class="form-control">
            </div>
            <div>
              <label for="userName">유저명</label>
              <input id="userName" type="text" name="userName" placeholder="유저명을 입력하세요" class="form-control">
            </div>
            <div>
              <label for="userEmail">email</label>
              <input id="userEmail" type="text" name="userEmail" placeholder="이메일을 입력하세요" class="form-control">
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

<script setup>
import { creaetLog } from "~/utils/userUtil";

const data = () => ({
    userId: 'userId',
    userPwd: 'userPwd',
    userName: 'userName',
    userEmail: 'userEmail',
    userAddress: '',
});

const userRegister = async () => {
        const param = {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
            },
            body: data,
        };
      creaetLog('REGISTER USER PARAM', param);
    const result = await fetch('http://localhost:8090/basic/user/userResist', param);
    creaetLog('REGISTER USER RES', result);
}
</script>