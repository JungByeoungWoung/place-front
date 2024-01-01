<template>
    <nav class="navbar navbar-expand-sm navbar-light bg-light">
        <div class="container-fluid">
            <NuxtLink to="/" class="navbar-brand" style="height:25px;">HOME</NuxtLink>
            <div style="flex-basis:100%;">
                <ul class="navbar-nav me-auto">
                    <li class="nav-item">
                        <NuxtLink to="/login" class="nav-link">Login</NuxtLink>
                    </li>
                    <li class="nav-item">
                        <NuxtLink to="userRegister" class="nav-link">회원가입</NuxtLink>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>
<style scoped>
nav .navbar-nav a.router-link-exact-active {
  color: #42b983 !important;
}
nav .navbar-nav a.nav-link {
  font-weight: bold;
  color: #2c3e50 !important;
}

nav .navbar-nav a.nav-link {
  font-weight: bold;
  color: #2c3e50 !important;
  text-align:initial;
}
</style>