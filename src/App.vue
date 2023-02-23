<template>

  <div v-if="1 == 2">
    안녕하세요
  </div>
  <div v-else-if="1 == 3">
    안녕하세요2
  </div>


  <div class="menu">
    <a v-for="(a,i) in 메뉴들" :key="i">{{ a }}</a>
  </div>

  <div class="discount" v-if="showDiscount == true">
    <h4>지금 결제하면 30% 할인</h4>
  </div>

  <button @click="priceSort">가격순정렬</button>
  <button @click="sortBack">되돌리기</button>

  <Card @openModal="모당창열렸니 = true; 누른거 = $event" :원룸="원룸들[i]" v-for="(작명,i) in 원룸들" :key="작명"/>


<transition name="fade">
  <Modal @closeModal="모달창열렸니 = false" :원룸들="원룸들" :누른거="누른거"
   :모달창열렸니="모달창열렸니" />
</transition>

</template>

<script>

import data from './assets/oneroom.js';
import Modal from './Modal.vue';
import Card from './Card.vue';


export default {
  name: 'App',
  
  data(){
    return{
      showDiscount : true,
      원룸들오리지널 : [...data],
      오브젝트 : { name : 'kim', age : 20},
      누른거 : 0,
      원룸들 : data,
      모달창열렸니 : false,
      신고수 : [0,0,0],
      메뉴들 : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
    }
  },

  methods : {
    increase(){
      this.신고수 +=1;
    },
    sortBack(){
      this.원룸들 = [...this.원룸들오리지널];
    },
    priceSort(){
      this.원룸들.sort(function(a,b){
        return a.price - b.price
      })
    },
  },


  mounted(){
    setTimeout(()=>{
      this.showDiscount = false;
    }, 2000);
  },

  components: {
    Modal : Modal,
    Card : Card,
  },
  
}
</script>

<style>
.fade-leave-from {
  opacity: 1;
  }
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}

.fade-enter-from {
  transform: translateY(-1000px);
  }
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  transform: translateY(0px);
}

body {
  margin : 0
}
div {
  box-sizing: border-box;
}
.discount{
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}

.black-bg {
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a{
  color: white;
  padding: 10px;
}
</style>
