<template>
    <!-- es5 -->
    <!-- '이미지'+ [i] -->
    <!-- es6 -->
    <!-- `이미지 ${[i]}` -->
    <!-- <img :src="원룸들[i].image" :alt="'이미지'+ [i]" class="room-img"> -->
    <!-- <h4  @click="모달창열렸니 = true; 누른거 = i">{{ item.title }}</h4> -->
    <!-- <h4>{{ item.title }}</h4> -->
    <!-- <p>{{ 원룸들[i].price }} 원</p> -->
    <div>
        <!-- <img :src="item.image" :alt="`이미지${[i + 1]}`" class="room-img"> -->
        <!-- <p>{{ item.price }} 원</p> -->
         <!-- <p>{{ 원룸들[i].price }} 원</p> -->
        <!-- <p>card test</p>
            <img :src="원룸들.image" :alt="`이미지${[i + 1]}`" class="room-img"> 
    <p>{{ 원룸들.price }} 원</p>  -->

     <img :src="item.image" :alt="`이미지${item.id + 1}`" class="room-img"> 
    <p>{{ item.price }} 원</p> 
    <p>{{ item.content }}</p>
    </div>
</template>

<script>

export default {
    name: 'Card',
    props: {
        item: Object   
    }
}

</script>