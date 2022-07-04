<template>
  <v-carousel
   cycle
   interval="10000"
   :show-arrows="false"
   hide-delimiters
   height="800"
  >
    <v-carousel-item v-for="item of items" :key="item.id">
      <v-container>
        <v-row>
          <v-col class="m-5">
            <img class="card-img-top" style="width:800px" :src="item._embedded['wp:featuredmedia'][0].source_url">
          </v-col>
          <v-col class="m-7">
          <div class="card-body">
            <v-card-title class="card-title">{{item.title.rendered}}</v-card-title>
            <v-card-text class="card-text" style="text-align:justify">{{item.excerpt.rendered}}</v-card-text>
          </div>
          </v-col>
        </v-row>
        </v-container>  
    </v-carousel-item>

  </v-carousel>

  
</template>

<script>
import { createSimpleTransition } from 'vuetify/lib/components/transitions/createTransition';
export default {
  name: "App",
  data() {
    return {
      items: [],
      nr:0
    };
  },
  created(){
    this.getRss();
  },

  methods: {
    async getRss() {
      const res = await fetch(
        `https://api.allorigins.win/get?url=https://www.borgleon.at/wp-json/wp/v2/posts?_embed`
      );
      const { contents } = await res.json();
      let items = JSON.parse(contents)
      items.forEach(el => {
 
        if(el._embedded['wp:featuredmedia'] !== undefined){
          this.items.push(el);
        }
      });
    },
  },
  mounted() {
        const newTransition = createSimpleTransition('new-transition');
        this.$once("hook:components", () => {
            newTransition
        })
        
    }
}
</script>
