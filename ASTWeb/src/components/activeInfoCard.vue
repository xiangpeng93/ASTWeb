<template>
  <div>
    <div style="margin:0px;padding:5px">
      <div class="row">
         <div class="col-sm-12 col-xs-12 col-md-12">
         <div class="thumbnail"style=" text-decoration: none;">
            <!--<img v-bind:src="imgUrl" 
             alt="图片信息">-->
           <a v-bind:href="href"   class="container img-responsive center-block img-rounded" :style="{backgroundImage:'url(' + imgUrl + ')'}" style=" background-size: cover; background-position: center; height:400px">
           </a>
           <div style="padding:10px;">
             <h3  class="text-center ">{{ head }}</h3>
             <p class="container">{{ body }}</p>
             <p>
             </p>
             <blockquote class="blockquote-reverse container">
               <footer>
                 Click in <cite title="Source Title">Pic Title</cite>
               </footer>
             </blockquote>
           </div>
         </div>
			</div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      head: String,
      body: String,
      imgUrl: String,
      href: String,
      required: true
    }
  }
</script>