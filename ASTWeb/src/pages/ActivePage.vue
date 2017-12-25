<template>
  <main-layout>
    <div class="container" style="padding-bottom:10px;">
      <h2 class="text-center" >{{ head }}</h2>
      <br>
        <p  style=" font-family: Helvetica;" >
         创建时间:{{ time }}  阅读次数:{{ count }}
		 <span class="pull-right">发布者:{{ auther }}</span> 
		 <br>
		
        </p>
      <hr>
        <span  v-html="body"></span>
        
	<div class="text-right">
		<button class="btn btn-primary" style="margin:5px;" @click="ActiveRegister()">报名请点击</button>
	</div>	
	
	<!-- Modal -->
<div class="container">
    <div class="modal fade" id="active_modal" tabindex="0" role="dialog" aria-labelledby="myModalLabel">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close"><span aria-hidden="true">&times;</span></button>
                    <h4 class="modal-title" id="myModalLabel">报名信息</h4>
                </div>
                <div class="modal-body" id="form_data" name="form_data">
                    <form id="form_active" name="form_active">
                        <div class="form-group">
                            <label >姓名</label>
                            <input type="text" class="form-control" id="name" name="name"
                                   placeholder="请输入姓名">
                        </div>
                        <div class="form-group">
                            <label >联系方式</label>
                            <input type="text" class="form-control" name="phoneNum"
                                   placeholder="请输入手机号码">
                        </div>
                        <div class="form-group">
                            <label >年龄</label>
                            <input type="text" class="form-control" name="ageNum"
                                   placeholder="请输入年龄">
                        </div>
                        <div class="form-group">
                            <label >参与时间段</label>
                            <input type="text" class="form-control" name="chooseTime"
                                   placeholder="请输入时间段，若无时间段选择，可不填写">
                        </div>
                    </form>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-default" data-dismiss="modal">取消</button>
                        <button type="button" id="active_push_btn" class="btn btn-primary">提交报名信息</button>
                    </div>
                </div>

            </div>
        </div>
    </div>
</div>

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
  data: function(){
  return {
  head: "",
  body: "",
  imgUrl: "",
  href: "",
  required: true
  }
  },
  methods:
  {
   GetQueryString :function(name){  
    var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)", "i");  
    var r = window.location.search.substr(1).match(reg);  //获取url中"?"符后的字符串并正则匹配
    var context = "";  
    if (r != null)  
         context = r[2];  
    reg = null;  
    r = null;  
    return context == null || context == "" || context == "undefined" ? "" : context;  
	},
	ActiveRegister : function()
	{
	console.log("-------"+document.body)
	
		$('#active_modal').modal('show');  
	}
  },
  mounted()
  {
	console.log(this.GetQueryString("id"))
	var submitUrl = "http://127.0.0.1:18080/AST/activeQuery";
	console.log(submitUrl);

	var htmlobj=$.ajax({ type: 'GET',url:submitUrl,data: {id:this.GetQueryString("id")},async:false});
	console.log(htmlobj.responseText);
	var resultData = JSON.parse(htmlobj.responseText);
	
	this.head=resultData.activeName;
	this.body=resultData.activeBody;
	this.time=resultData.activeTime;
	this.count = resultData.activeReadCount;
	this.auther = resultData.activeAuthor;
	

  }
  }
</script>
