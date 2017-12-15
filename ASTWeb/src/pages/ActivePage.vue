<template>
  <main-layout>
    <div class="container" >
      <h2 >{{ head }}</h2>
      <br>
        <p  style=" font-family: Helvetica;">
         创建时间：{{ time }} &nbsp;  &nbsp; 阅读次数：{{ count }}  &nbsp; &nbsp; <span class="pull-right">作者：{{ auther }}</span>
        </p>
      <hr>
        <p>{{ body }}</p>
        
        <br>
        <br>
    </div>
</div>
  </main-layout>
</template>

<script>
  import MainLayout from '../layouts/Main.vue'
  export default {
  components: {
  MainLayout
  },
  props: {
  head: String,
  body: String,
  imgUrl: String,
  href: String,
  required: true
  },
  mounted()
  {
  this.head="活动名称";
  this.body="活动内容";
  this.time="2017-12-15 13:33:00";
  this.count = "123";
  this.auther = "XP";

  if($("html").height() > $("#mainDiv").height())
  {
  $("#mainDiv").css("height","100%");
  }

  }
  }
</script>
