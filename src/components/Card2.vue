<template>
    <div>
    <img :src="taking.image" :alt="`이미지${taking.id + 1}`" class="room-img"> 
    <p>{{ taking.price }} 원</p> 
    <p>{{ taking.content }}</p>
    
    <h4 @click="$emit('openModal', taking.id)">{{ taking.title }}</h4>
    <!-- $emit('작명','데이터') 자식컴포먼트가 부모한테 보내는 것 -->
</div>

</template>

<script>
export default {
    name: 'Card2' ,

    props: {
        taking : Object,
    },
    methods : {
        send(){
            this.$emit('openModal',this.원룸.id)
            //@click="$emit('openModal', taking.id)" 이거 대신에 함수를 넣을 수 있음
        }
    }

}
</script>