<template>
  <main-layout>
	<div class="text-center">
		<h2>信息发布平台</h2>
	</div>
	<hr>
	<div class="container">

	<div class="form-group">
		<!-- Text input-->
		<label  for="UserName">活动标题</label>
		<br/>
		<input id="active_name" name="active_name" type="text" placeholder="输入标题" class="form-control">
	</div>
	<div class="form-group">
		<!-- Text input-->
		<label>活动场次数量</label>
		<br/>
		<input id="active_size" name="active_name" type="text" placeholder="输入数量" class="form-control">
	</div>
	<div class="form-group">
		<!-- Text input-->
		<label>每场人数限制</label>
		<br/>
		<input id="active_person_size" name="active_name" type="text" placeholder="输入人数" class="form-control">
	</div>

	</div>
	<hr>
	<div id="editDivHead">
	</div>
	<div name="active_body" id="editDivBody" style="height:500px;margin:5px;">
		
	</div>

	<hr>
	<div class="text-right">
	<button class="btn btn-primary " style="margin:5px;" @click="AddActiveInfo()">保存并发布信息</button>
	</div>	
</main-layout>
</template>

<style scoped>
  @import '../../wang/wangEditor.css';
</style>

<script>
  import wangEdit from '../../wang/wangEditor.js';
  import MainLayout from '../layouts/Main.vue';
  
  var editor2 = new wangEdit('#editDivHead','#editDivBody');

  export default {
  components: {
  MainLayout
  },
  mounted(){
  this.createEdit();
  
  
  },
  methods: {
  createEdit: function () {
  //editor2.customConfig.uploadImgShowBase64 = true   // 使用 base64 保存图片
  editor2.customConfig.uploadImgServer = 'http://127.0.0.1:18080/AST/uploadPic'  // 上传图片到服务器
  editor2.customConfig.zIndex = 1
  editor2.create()
  },
  
  getEditText: function () {
  console.log("get edit");
  console.log(editor2.txt.html());
  },
  
  AddActiveInfo: function () {
	var submitUrl = "http://127.0.0.1:18080/AST/activeAdd";
	console.log(submitUrl);
	
	var htmlobj=$.ajax({ type: 'POST',url:submitUrl,dataType:'json',data: {active_name:$("#active_name").val(),active_body:editor2.txt.html()},async:false});
	alert(htmlobj.responseText);
  }
  }
  }
</script>
