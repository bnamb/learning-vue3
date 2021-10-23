<template>
   <div class="relative flex flex-wrap w-full text-gray-700">
       <div class="m-auto">
       <h1 class="text-3xl w-full my-4">Slider Carousel</h1>
       </div>
       <div v-for="(color,index) in sliders" :key="color" class="absolute pt-16 w-full">
            <transition name="fade">
                <div v-if="currentSlide == index" :class="color" style="height: 350px"></div>
            </transition>
       </div>
       <div class="w-full" style="height: 340px">
            <div class="absolute bottom-0 w-full flex justify-center">
                <div 
                v-for="(slider, index) in sliders" 
                @click="makeActive(index)" 
                :key="slider" 
                :class="currentSlide == index ? 'bg-gray-700' : 'bg-gray-300'" 
                class="mx-2 w-4 h-4 rounded-full bg-black cursor-pointer shadow-md" ></div>
            </div>
       </div>
       <!-- <div class="my-10 flex w-full">
           <div class="m-auto">
               <transition name="fade">
                   <h1 v-if="isTextShowing">Slider Carousel</h1>
               </transition>
               <button @click="isTextShowing = !isTextShowing" class="px-2 rounded border">Toggle Text</button>
           </div>
       </div> -->
   </div>
</template>

<script>
export default {
    data(){
        return {
            currentSlide: 0,
            interval: "",
            sliders:["bg-green-500","bg-yellow-300","bg-pink-500"],
            isTextShowing: true,
        }
    },
    methods: {
        makeActive(index){
            this.currentSlide = index;
            
        }
    },
    mounted(){
        this.interval = setInterval(() => {
            this.currentSlide = this.currentSlide === 2 ? 0 : this.currentSlide + 1;
        }, 2000);
    },
    beforeUnmount(){
        clearInterval(this.interval);
    },
};
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: all 1s ease;
}

.fade-enter-from {
    opacity: 0;
    transform: translateX(-100%);
}
.fade-leave-to {
  opacity: 0;
  transform: translateX(100%);
}
</style>