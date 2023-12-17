<template>
    <div>
        <NavigationBar />
        <div class="row">
            <div class="col-md-6 mt-5 mx-auto">
                <form action="/basic/user/userResist" method="post">
                  <h2 class="h3 mb-3 font-weight-normal">로그인 페이지</h2>
                  <div class="form-group">
                    <label for="userId">유저 ID</label>
                    <input id="userId" type="text" name="userId" placeholder="유저아이디를 입력하세요" class="form-control">
                  </div>
                  <div class="form-group">
                    <label for="userPwd">비밀번호</label>
                    <input id="userPwd" type="text" name="userPwd" placeholder="비밀번호를 입력하세요" class="form-control">
                  </div>
                  <hr class="my-4">
                    <div class="row">
                    <div class="col">
                    <button id="login" class="btn btn-lg btn-primary btn-block" type="submit" >로그인</button>
                  </div>
                </div>
              </form>
            </div>
        </div>
    </div>
</template>