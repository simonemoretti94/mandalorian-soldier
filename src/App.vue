<script>
export default {
  name: 'app',
  data() {
    return {
      activeSlide: 0,
      slider: {
        name: 'Mandalorian',
        images: [
          'https://image.tmdb.org/t/p/original/9zcbqSxdsRMZWHYtyCd1nXPr2xq.jpg',

          'https://image.tmdb.org/t/p/original/aZ4fmjMUAhS6PWhVLDDfT0RAdNe.jpg',

          'https://image.tmdb.org/t/p/original/p7fwOnlxYYlB4A8U2b0JfX21Rr1.jpg',

          'https://image.tmdb.org/t/p/original/qruRhG6jE5M8lWnW1AGOBxtdmCO.jpg',

          'https://image.tmdb.org/t/p/original/lMu3y10KgIYtXFPeCMim3D8iihV.jpg'

        ],
        category: 'Action',
        length: 40,


      },
      /* scale F variable */
      classScale1: '',
      classScale2: '',

      counter1: 0,
      counter2: 0,

      //thumb variables
      thumb1: 'thumbnail1',
      thumb2: 'thumbnail2',
    }
  },
  methods: {
    mounted() {
      console.log(this.slider)
    },
    prev() {
      console.log('prev');
      this.activeSlide--;

      if (this.activeSlide < 0) {
        this.activeSlide = (this.slider.images.length - 1);
      }

    },
    next() {
      console.log('next');
      this.activeSlide++;

      if (this.activeSlide > this.slider.images.length - 1) {
        this.activeSlide = 0;
      }
    },
    scaleF1() {
      this.counter1++;
      if (this.counter1 % 2 !== 0) {
        this.classScale1 = 'scale';
      }
      else {
        this.classScale1 = '';
      }
    },
    scaleF2() {
      this.counter2++;
      if (this.counter2 % 2 !== 0) {
        this.classScale2 = 'scale';
      }
      else {
        this.classScale2 = '';
      }
    }
  },

}

</script>

<template >
  <div class="container d-flex  flex-column justify-content-evenly align-items-center">

    <!-- FIRST BLOCK -->


    <div class="container">

      <!-- Mandalorian title -->
      <h1 class="text-center text-white display-2 text-shadow">{{ slider.name }}</h1>

      <!-- DIV element containing carousel -->
      <div class="card">
        <img :src="slider.images[activeSlide]" alt="slider">
      </div>
      {{ mounted() }}

    </div>

    <!-- SECOND BLOCK -->

    <!-- DIV ELEMENT CONTAINING THUMBNAILS -->
    <div class="col-12 d-flex flex-row justify-content-evenly mt-2">
      <img v-bind:class="index === activeSlide ? thumb1 : thumb2" :src="thumbnail"
        v-for="(thumbnail, index) in slider.images" :alt="`mandalorian-` + index" :key="`mandalorian-` + index">
    </div>



    <!-- THIRD BLOCK -->

    <!-- DIV element containing shifting buttons -->
    <div class="col-8 navigator d-flex justify-content-between mt-2 mx-auto">

      <button class="btn display-1 border rounded-2 text-center bg-warning me-1" :class="classScale1"
        @mouseenter="scaleF1()" @mouseleave="scaleF1()" @click="prev()">Previous</button>

      <button class="btn display-1 border rounded-2 text-center bg-success ms-1" :class="classScale2"
        @mouseenter="scaleF2()" @mouseleave="scaleF2()" @click="next()">Next</button>

    </div>
  </div>
</template>

<style >
.scale {
  transform: scale(.9);
}

div.navigator>button:hover {
  cursor: pointer;
}

#btn-1,
#btn-2 {
  font-size: x-large;
  color: white;
  border: 1px solid rgb(87, 87, 87);
  border-radius: 8px;
  height: 50px;
  width: 90px;
}

#btn-1 {
  background-color: rgb(0, 178, 0);
  margin-right: .5rem;
}

#btn-2 {
  background-color: rgb(214, 0, 0);
  margin-left: .5rem;
}

.thumbnail1 {
  width: ((100% / 5)- 30px);
  height: 100px;
  border: solid .5px white;
  border-radius: 5px;
}

.thumbnail2 {
  width: ((100% / 5)- 30px);
  height: 100px;
  border: solid .5px white;
  border-radius: 5px;
}
</style>
