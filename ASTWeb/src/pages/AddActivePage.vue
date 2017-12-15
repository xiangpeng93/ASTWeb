<template>
  <main-layout>
	<div class="text-center">
		<h2>信息发布平台</h2>
	</div>
		<hr>
      
	<div id="editDivHead">
	</div>
	<div id="editDivBody" style="height:500px;margin:5px;">
			
	</div>
	<hr>
	<div class="text-right">
	<button class="btn btn-primary " @click="getEditText()" style="margin:5px;">保存并发布信息</button>
	</div>	
</main-layout>
</template>

<style scoped>
  @import '../../wang/wangEditor.min.css';
</style>

<script>
  import wangEdit from '../../wang/wangEditor.min.js';
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
  editor2.customConfig.uploadImgServer = '/upload'  // 上传图片到服务器
  editor2.customConfig.zIndex = 1
  
  editor2.create()

  },
  getEditText: function () {
  console.log("get edit");

  console.log(editor2.txt.html());
  }
  }
  }
</script>
