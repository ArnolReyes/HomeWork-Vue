<template>    
    <v-row id="rowStartPreviewCard">         
        <v-col v-if="imageMobile" lg="6" md="12" sm="12" class="colImage"  >                
                 <v-img :style="stylesImgMobile">
                </v-img>
        </v-col> 
        <v-col id="contentText" lg="6" md="12" sm="12">
            <v-col cols="12 font-inter title-style">
                <p>Get <span id="spnImportantText">insights</span> that help
                your bussines grow.
             </p>

            </v-col>  
            <div class="col-12 font-lexend-deca body-text"> 
                <span> Discover the benefits of data analytics and make better decisions regarding revenue, customer experience, and
                    overall efficiency. </span>                
            </div>

            <v-col cols="12" id="divFooter">
                <v-col lg="4" md="4" sm="4">
                <span> 10k+ </span>
                <p> COMPANIES </p>
                </v-col>

                <v-col lg="4" md="4" sm="4">
                <span> 314 </span>
                <p> TEMPLATES  </p>
                </v-col>

                <v-col lg="4" md="4" sm="4">
                <span> 12M+ </span>
                <p> QUERIES </p>
                </v-col>
            </v-col>

        </v-col>
         
        <v-col v-if="imageDesktop" lg="6" md="12" sm="12" class="colImage">                                           
                <v-img :style="stylesImgDesktop">
                </v-img>
        </v-col>         
    </v-row>
</template>

<script>

import image from '../../images/image-header-desktop.jpg';

export default {    
data: () => ({        
    imagePath:'linear-gradient(rgb(161 14 255 / 41%) 100%,rgb(0 0 0 / 0%)100%), url('+image+')'
 }),
   
 props:{
    imageMobile:Boolean,  
    imageDesktop:Boolean   
 },

computed:{
  stylesImgDesktop: function() {
    return {          
      'border-radius': '0em 1em 1em 0em',
      'background-image':this.imagePath,
      'width': '100%',
      'height': '100%',      
      'background-size': 'cover',      
      'background-repeat': 'round',
      'opacity': '0.8',
    }
  },

  stylesImgMobile: function() {
    return {          
      'background-image':this.imagePath,
      'width': '100rem',
      'height': '15rem',  
      'background-size': '100% 100%',      
      'max-width': '100%',
      'opacity': '0.8',
    }
  },
  
},

methods: {
  myEventHandler(e) {          
      const showImage = e.target.innerWidth<=1263;      
      this.$emit("show-image",showImage);                  
  }  
},
created() {
  window.addEventListener("resize", this.myEventHandler);  
},
destroyed() {
  window.removeEventListener("resize", this.myEventHandler);
},

mounted(){
    const showMobileImage = window.innerWidth<=1263;    
    this.$emit("show-image",showMobileImage); 
},

}
</script>

<style lang="scss" scoped>

@import '../../Styles/_style';

@media screen and (max-width: 1263px) {
    .colImage *{ 
        border-radius: 1rem 1em 0rem 0rem !important;
    }
}

@media screen and (max-width: 500px) {    
.title-style{
    padding: 0.8em 0em 0.3em 0em;
}

#rowStartPreviewCard{
    & {      
    #contentText{
        padding:1em !important;
        text-align: center;
    }
    #divFooter{            
        display: initial !important;
         }
    }
  }    
}

#rowStartPreviewCard{
    background-color:hsl(244, 38%, 16%); 
    border-radius: 1em;
    &{
       #contentText{
         padding: 3.5em 5.5em 0em 5.5em
       }
       #spnImportantText{
        color:hsl(277, 64%, 61%);
       }
       .colImage{
         padding: 0px;         
         & div{
             border-radius: 0 1em 1rem 0;
             height: 100%;
         }
        }  
        #divFooter{
            justify-content: center;
            display: flex;
            padding: 4em 0em 2em 0em;
            & span{              
                font-weight: bold;
                color: white;
                font-size: 1.5em;
                font-family: 'Inter';
                margin-bottom: 1em;
            }
            & p{       
                margin-top:0.5em;         
                font-size: 0.8em;
                color:hsla(0, 0%, 100%, 0.6);
                font-family: 'Lexend Deca';
            }
        } 
    }
}

</style>