<template>
  <div class="">
    <h3>CalculatorView3</h3>
    <input type="text" v-model="num1" ><span>+</span>
    <input type="text" v-model="num2" ><span>=</span>
    <span>{{result}}</span>
  </div>
</template>

<script>
import {reactive, computed, toRefs} from 'vue';

function plusNumbers(){
    //반응형 상태객체: 속성변경될때마다 자동으로 DOM업데이튼
    let state = reactive({
      num1:0, //첫번째 텍스트박스와 바인딩될 숫자
      num2:0, //두번째 텍스트박스와 바인딩될 숫자
      result:computed(()=>Number(state.num1)+Number(state.num2))
      //계산된 결과를 저장할 상태
    });
    //toRefs : 반응형 상태객체 -> 일반 자바스크립트 객체로 변경
    return toRefs(state);
}
export default {
  name: 'CalculatorView3',
  setup(){
    //구조분해할당으로 num1,num2,result값을 얻기
    let{num1,num2,result}=plusNumbers();
    //구조분해된 변수값을 반환
    return{num1,num2,result};
  }
};
</script>

<style scoped>
/* 스타일을 추가하세요 */
</style>