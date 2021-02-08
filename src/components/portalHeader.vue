
<template>
  <div class="vue-tempalte" style="height: auto">
    <!-- Navigation -->
    <nav class="navbar  bg-white justify-content-between flex-nowrap flex-row">
      <div class="container">
        <div class="navbar-brand float-left">
           <h3>Job Portal</h3>
        </div>
        <ul class="nav navbar-nav flex-row float-right">
          <li class="nav-item">
            <router-link class="nav-link pr-3" to="/">Sign in</router-link>
          </li>
          <li class="nav-item">
            <router-link class="btn btn-outline-primary" to="/signup">Sign up</router-link>
          </li>
          <!-- <li class="nav-item">
            <router-link class="btn btn-danger" to="/logout">Log Out</router-link>
          </li> -->
        </ul>
      </div>
    </nav>
</div>
</template>

<script>
export default {
    
}
</script>
