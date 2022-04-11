<template>
  <div class="row" style="background: #1ba6e2; color: white; text-align: center; height: 60px">
    <div class="col m-auto" style="text-align: left">
      <img style="height: 60px" src="../assets/navbar.png">

      <img src="../assets/logo.png">
    </div>
    <div class="col text-center" style="margin: auto;"><h4>{{ MenuData.meta.titleBar }}</h4></div>
    <div class="col">
      <div style="float: right; text-align: center; margin-top: 18px; margin-right: 15px">
        <a style="text-decoration: none; color: white" href="https://secure.postimees.ee/login">LOGI</a>
        <a style="text-decoration: none; color: white" href="https://secure.postimees.ee/login/register">SISSE</a>
      </div>
      <div style="float: right; margin-right: 100px; margin-top: 8px; font-size: 22px">
        <a :href="MenuData.meta.social.facebook"><img src="../assets/Facebook.png" alt="Facebook"></a>
        <a :href="MenuData.meta.social.twitter"><img src="../assets/Twitter.png" alt="Twitter"></a>
        <a href=""><img src="../assets/Email.png" alt="Email"></a>
        <img style="padding-left: 30px" src="../assets/comments.png">
            88
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      MenuData: []
    }
  },
  async fetch() {
    this.MenuData = await fetch(
      'https://services.postimees.ee/rest/v1/sections/81'
    ).then(res => res.json())
  },
  mounted() {
    let jquery = document.createElement('script')
    let bootstrap = document.createElement('script')
    jquery.setAttribute('src', 'https://code.jquery.com/jquery-3.3.1.slim.min.js')
    bootstrap.setAttribute('src', 'https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js')
    document.head.appendChild(jquery)
    document.head.appendChild(bootstrap)
  }
}
</script>

