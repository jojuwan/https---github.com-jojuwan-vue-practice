<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div calss="white-bg"> 
      <img :src="원룸들[누른거].image" style="room-ing">
      <h4>{{원룸들[누른거].title}}</h4>
      <p>{{원룸들[누른거].content}}</p>
      <p>{{원룸들[누른거].price}} 원</p>
      <input v-model="month">
      <p> {{ month }} 개월 선택함 : {{원룸들[누른거].price * month}} 원</p>
      
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
    name : 'Modal',
    data(){
      return {
        month : '',
      }
    },
    watch: {
      month(a){
        if(a != ''){
          alert('글자입력하지마셈')
        }
        
      },
    },
    props : {
        원룸들 : Array,
        누른거 : Number,
        모달창열렸니 : Boolean,
    }
}
</script>

<style>

</style>