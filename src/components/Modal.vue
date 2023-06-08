<template>
    <div class="black-bg" v-if="모달창열렸니 == true">
        <div class="white-bg" >
            <img :src="원룸들[누른거].image" :alt="`이미지${[i]}`" class="room-img">
            <h4>{{ 원룸들[누른거].title }} </h4>
            <p>{{ 원룸들[누른거].content }}</p>
            <!-- <input @input="month = $event.target.value"> -->
            <input v-model.number="month">
            <!-- 문자를 막는 뜻은 아니고 넘버를 사용하게하는것 -->
            
            <p>{{ month }} 개월 선택함 :  {{ 원룸들[누른거].price * month}}</p>
            <button @click="$emit('close')">닫기</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Modal',
    data() {
        return {
            month: 1,
        }
    },
    watch: {
        //data 안에 month를 감시하는 것 같은 내 이름 사용
        month(a){
            if (isNaN(a)){
                alert('문자입력하지마세요');
                this.month = 1
            }else if(a > 13){
                // 사용자가 month를 글자로 입력하면 경고문띄워주셈
                alert('13이상 입력하지 마세요')
            }
        }
    },
    props: {
        원룸들 : Array,
        누른거 : Number,
        모달창열렸니 : Boolean,
    },
}



</script>
