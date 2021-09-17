<template >
    <v-main >
      <v-card id="mainStyles">        
          <StatsPreviewCard 
          :imageMobile="imageMobile"
          :imageDesktop="imageDesktop"
           @show-image="showMobileImage"
          />
      </v-card>
      
    </v-main>

</template>

<script>
import StatsPreviewCard from './components/StatsPreviewCard';

export default {
  name: 'App',

  components: {
    StatsPreviewCard,
  },

  data: () => ({
    imageMobile:false,
    imageDesktop:true
  }),

  methods:{
      showMobileImage(value){
       this.imageMobile=value
       this.imageDesktop = !value
      } 
   }

};
</script>

<style lang="scss" scoped>

@media screen and (max-width: 767px) {
    #mainStyles{
        padding:6em 2em !important;
    }
}

 #mainStyles{
   background-color: hsl(233, 47%, 7%);
   padding: 8em;
 }

</style>





