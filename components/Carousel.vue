<template>
    <div class="carousel-wrapper">
        <div class="carousel-inner-box">
            <transition-group class="carousel" tag="div">
                <div v-for="slide in slides" :key='slide.id' class="slide">
                    <div class="slide-title"><h4>{{slide.title}}</h4></div>
                    <div class="slide-image">{{slide.image}}</div>
                    <div class="slide-description"><p>{{slide.description}}</p></div>
                </div>
            </transition-group>
        </div>
        <div class="carousel-controls">
            <button class="button-prev" @click="prev">prev</button>
            <button class="button-next" @click="next">next</button>
        </div>
    </div>
</template>
<script>
export default {
  name: 'Carousel',
  data(){
      return{
          slides: [
              {
                  id: 1,
                  title: 'Slide 1',
                  image: 'Image 1',
                  description: 'short descryption of a case 1'
              },
              {
                  id: 2,
                  title: 'Slide 2',
                  image: 'Image 2',
                  description: 'short descryption of a case 2'
              },
              {
                  id: 3,
                  title: 'Slide 3',
                  image: 'Image 3',
                  description: 'short descryption of a case 3'
              },
              {
                  id: 4,
                  title: 'Slide 4',
                  image: 'Image 4',
                  description: 'short descryption of a case 4'
              },
              {
                  id: 5,
                  title: 'Slide 5',
                  image: 'Image 5',
                  description: 'short descryption of a case 5'
              },
          ]
      }
  },
  methods:{
      prev(){
          const last = this.slides.pop();
          this.slides = [last].concat(this.slides);
      },
      next(){
          const first = this.slides.shift();
          this.slides = this.slides.concat(first); 
      }
  }  
}
</script>
<style>
    .carousel-wrapper {
        display: flex;
        flex-direction: column;
        align-items: center;
        
    }
    .carousel-inner-box{
        background-color: #000;
        display: flex;
        justify-content: center;
    }
    .carousel {
        display: flex;
        justify-content: center;
        align-items: center;
        overflow: hidden; 
        width: 100vw;
        height: 500px;
        background-color: #000;
    }
    .slide {
        flex: 0 0 100vw;
        height: 500px;
        display: flex;
        flex-direction: column;
        padding: 0px;
        align-items: center;
        transition: transform .4s ease-in-out;
    }
    .slide-title{
        height: 60px;
        background-color: yellow;
        width: 100%;
        display: flex;
        align-items: center;
    }
    .slide-title h4{
        margin-left: 20px;
    }
    .slide-image{
        margin: 2px 0;
        width: 100%;
        height: 480px;
        background-color: #fff;
    }

    .slide-description{
        width: 100%;
        height: auto;
        background-color: #fff;
        flex-grow: 1;
        display: flex;
        align-items: center;
        justify-content: left;
    }
    .slide-description p{
        margin-left: 20px;
    }
    .slide:first-of-type {
    opacity: 0;
    }
    .slide:last-of-type {
    opacity: 0;
    }
    @media screen and (min-width: 600px){
         .carousel-inner-box{
            width: 500px;
            height: 500px;
        }
        .carousel{
            width: 480px;
            height: 500px;
        }
        .slide{
            flex: 0 0 480px;
            height: 500px;
            padding: 10px 0;
        }
        .slide-image{
            margin: 10px 0;
            height: 320px;
        }
    }
    @media screen and (min-width: 1200px){
        .carousel-inner-box{
            width: 700px;
            height: 700px;
        }
        .carousel{
            width: 660px;
            height: 700px;
        }
        .slide{
            flex: 0 0 660px;
            height: 700px;
            padding: 20px 0;
        }

        .slide-title{

        }

        .slide-image{
            margin: 20px 0;
            height: 480px;
        }
        .slide-description{

        }
    }
</style>
