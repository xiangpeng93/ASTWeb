<template>
  <div>
    <div class="media col-md-6" style="margin:0px;padding:5px">
      <div class="row">
        <div class="col-md-8 col-xs-8">
          <div class="media-left">
            <a href="#">
              <img class="media-object" v-bind:src="imgUrl" alt="...">
		      </a>
          </div>
          <div class="media-body">
            <h4 class="media-heading">{{ head }}</h4>
            <p>{{ body }}</p>
          </div>

        </div>
        <div class="col-md-4 col-xs-4">
          <div class="row">
            <button class="btn btn-default col-md-8 " style="margin:5px;">编辑</button>
            <button class="btn btn-default btn-danger col-md-8" style="margin:5px;">删除</button>
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