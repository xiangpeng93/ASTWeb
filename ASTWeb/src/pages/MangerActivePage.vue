<template>
  <main-layout>
    <div class="container">
      <ul>
        <li :is="item.component" :head="item.headText" :body="item.bodyText" :imgUrl="item.imgUrl"  v-for="item in items"></li>
      </ul>
    </div>
  </main-layout>
</template>

<script>
  import MainLayout from '../layouts/Main.vue'
  import TitleCard from '../components/titleCard.vue'

  export default {
  components: {
  MainLayout,
  'TitleCard':TitleCard,
  },
  data() {
  return {
  items: [],
  }
  },
  mounted()
  {
    for(var i = 0; i < 10; i++)
      {
       console.log('-----');
       this.items.push({
        'component': 'TitleCard',
        'headText': 'Head',
        'bodyText': 'Body',
        'imgUrl': 'img/media1.jpg'
      });
       console.log(this.items);
      
      }
    }
  }

</script>
