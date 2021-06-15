<template>
  <h1>{{ msg }}</h1>
  
  <!-- v-model -->

  <!-- 단방향 데이터 바인딩, handler 메소드 이용하여 양방향 데이터 바인딩으로 -->
  <input 
    type="text"
    :value="msg" 
    @input="handler"/>
  
  <!-- inline 방식으로 작성, 양방향 데이터 바인딩, 한글 입력 시는 이 방법을 사용할 것 -->
  <input 
    type="text"
    :value="msg" 
    @input="msg = $event.target.value"/>
  
  <!-- v-model 디렉티브 이용, 간소화- -->
  <input 
    type="text"
    v-model="msg"/>
  
  <!-- msg가 숫자 데이터 일 때 숫자 데이터 타입으로 유지하고 싶을 때 사용-->
  <input 
    type="text"
    v-model.number="msg"/>

  <!-- 띄어 쓰기가 있을 때 띄어쓰기를 없애고(앞뒤 공백 제거) 출력 -->
  <input 
    type="text"
    v-model.trim="msg"/>

  <!-- @change : 입력 하고 있는 동안은 갱신x, enter나 tab을 눌러야 갱신됨 -->
  <input 
    type="text"
    :value="msg" 
    @change="msg = $event.target.value"/>

  <input 
    type="text"
    v-model.lazy="msg"/>
  

<!-- button -->
  <h1> {{ checked }} </h1>
  <input 
    type="checkbox"
    v-model="checked"/>
</template>

<script>
export default {
 data() {
    return {
      msg: 'Hello world!',
      // msg: 123,
      checked: false
    }
  },
    // 단방향 데이터 바인딩을 input이벤트를 발생시켜 handler메소드를 실행시킨다.
    // 반응성을 통해 해당 화면의 내용을 바꿔준다 즉, 양방향 데이터 바인딩이 일어난다.
  methods: {
    handler(e){
      console.log(e.target.value)
      this.msg = e.target.value
    }
  },
  watch: {
    msg() {
      // msg가 숫자일 때
      console.log(typeof this.msg)
      console.log(this.msg.trim())  //  띄어쓰기 제거
    }
  }
}
</script>